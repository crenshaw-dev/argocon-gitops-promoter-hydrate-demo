
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 3c362767478e23ea8e54e0baecab14238f9cb4f3
kustomize build ./user-configuration/staging/integration
```