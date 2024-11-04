
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 4c552ef623c6ec00b0b4c53b1772a7da03730fa3
kustomize build ./user-configuration/staging/e2e
```