
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout da49701edb08d85e0b06ffa089ec719b38c1daad
kustomize build ./user-configuration/production/us-west-1
```