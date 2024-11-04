
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 2ab072a32a4fd923604c40a2c14d986a66b7a359
kustomize build ./user-configuration/production/us-west-1
```