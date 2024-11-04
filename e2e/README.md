
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout e9e1e41b73b44a4b6a37bd386955634970956243
kustomize build ./user-configuration/staging/e2e
```