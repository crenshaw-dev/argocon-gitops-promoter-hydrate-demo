
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 78e18de3cb8daf8e94c8368300b6a14234eb00d5
kustomize build ./user-configuration/development
```