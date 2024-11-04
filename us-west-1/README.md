
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 64b32332f3c3306eef4c34d7567e885aadc7e743
kustomize build ./user-configuration/production/us-west-1
```