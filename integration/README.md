
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 782b129290fbc3b965175e1345be24314968974d
kustomize build ./user-configuration/staging/integration
```