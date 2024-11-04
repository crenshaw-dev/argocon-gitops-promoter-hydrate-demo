
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 18ea238236e308a398ac782172c5eab5c7333d82
kustomize build ./user-configuration/staging/integration
```