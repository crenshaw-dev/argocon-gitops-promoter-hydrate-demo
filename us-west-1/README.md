
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 54eff5e1b0de26b0e116cfd9360a30c03994d8a9
kustomize build ./user-configuration/production/us-west-1
```