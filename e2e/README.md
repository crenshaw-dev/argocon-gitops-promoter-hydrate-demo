
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 97b53454c89fb08b6004d0523e283983b3616b35
kustomize build ./user-configuration/staging/e2e
```