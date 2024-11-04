
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout dce0826ac6ef6b9f9b6677edffcc79c25856d4a9
kustomize build ./user-configuration/development
```