# GitOps Promoter Demo, ArgoCon NA 2024

## Set up a local cluster

We used Rancher Desktop for this demo, but any local cluster will work.

## Fork this repository

Fork this repo to your own GitHub account.

## Install GitOps Promoter

```shell
kubectl apply -k demo-configuration/promoter -n promoter-system
```

## Install Argo CD (with Hydrator)

```shell
kubectl create namespace argocd
kubectl config set-context --current --namespace=argocd
kustomize build demo-configuration/argocd | sed 's/zachaller/<your GitHub username>/g' | kubectl apply -f -
argocd admin initial-password  # You'll need this to log into the UI.
kubectl port-forward svc/argocd-server 8443:443
```

Then load the Argo CD UI at [http://localhost:8443](http://localhost:8443).

## Install Argo Rollouts

```shell
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
```

## Install Promoter and Argo resources

### Create an overlay to apply fork-specific changes

```shell
mkdir my-overlay
```

Create the following file in my-overlay/kustomization.yaml, replacing `<your GitHub username>` with your GitHub username:

```yaml
resources:
- ../demo-configuration/argocd-applications

patches:
- target:
    group: argoproj.io
    kind: Application
    name: development
  patch: |-
    - op: replace
      path: /spec/sourceHydrator/drySource/repoURL
      value: https://github.com/<your GitHub username>/argocon-gitops-promoter-hydrate-demo
- target:
    group: argoproj.io
    kind: Application
    name: production-use2
  patch: |-
    - op: replace
      path: /spec/sourceHydrator/drySource/repoURL
      value: https://github.com/<your GitHub username>/argocon-gitops-promoter-hydrate-demo
- target:
    group: argoproj.io
    kind: Application
    name: production-usw1
  patch: |-
    - op: replace
      path: /spec/sourceHydrator/drySource/repoURL
      value: https://github.com/<your GitHub username>/argocon-gitops-promoter-hydrate-demo
- target:
    group: argoproj.io
    kind: Application
    name: e2e-staging
  patch: |-
    - op: replace
      path: /spec/sourceHydrator/drySource/repoURL
      value: https://github.com/<your GitHub username>/argocon-gitops-promoter-hydrate-demo
- target:
    group: argoproj.io
    kind: Application
    name: integration-staging
  patch: |-
    - op: replace
      path: /spec/sourceHydrator/drySource/repoURL
      value: https://github.com/<your GitHub username>/argocon-gitops-promoter-hydrate-demo
```

```shell
kustomize build my-overlay | kubectl apply -n argocd -f -
```

Go to the [promotion strategy app](https://localhost:8443/applications/argocd/promotion-strategy?view=tree) and sync it.

## Create a GitHub app

[Create a new GitHub app](https://github.com/settings/apps/new) with the following permissions:

* r/w commit status
* r/w contents
* r/w pull requests

Disable the webhook.

After creating the app, generate a private key and save it to private-key.pem.

### Install the app

Install the app in the demo fork repository. After you install the app, the installation ID will appear in the URL. Copy this ID.

### Set up the promoter

Create a secret with the private key, the installation ID, and the app ID.

```shell
kubectl create secret -n promoter-system generic argo-app \
  --from-literal=privateKey="$(cat private-key.pem)" \
  --from-literal=installationID=<your installation ID here> \
  --from-literal=appID=<your app ID here>
```

Create the same secret in the `argocd` namespace for CommitStatuses.

```shell
kubectl create secret -n argocd generic argo-app \
  --from-literal=privateKey="$(cat private-key.pem)" \
  --from-literal=installationID=<your installation ID here> \
  --from-literal=appID=<your app ID here>
```

### Set up the hydrator

Create a secret with the private key, the installation ID, and the app ID.

```shell
kubectl create secret -n argocd generic hydrator-app \
  --from-literal=type=git \
  --from-literal=url=https://github.com/<your GitHub username>/argocon-gitops-promoter-hydrate-demo \
  --from-literal=githubAppPrivateKey="$(cat private-key.pem)" \
  --from-literal=githubAppInstallationID=<your installation ID here> \
  --from-literal=githubAppID=<your app ID here>
kubectl label secret -n argocd hydrator-app argocd.argoproj.io/secret-type=repository-write
```
