
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout a1ed14ddd01ea352999b3fd6f2c20828f55f5a3c
kustomize build ./user-configuration/development
```