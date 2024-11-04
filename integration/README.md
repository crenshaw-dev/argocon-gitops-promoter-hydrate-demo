
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 052b255704f2069ab195e7be68d11c7b3d90b30d
kustomize build ./user-configuration/staging/integration
```