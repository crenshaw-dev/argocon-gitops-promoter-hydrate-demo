
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout c79d0f1f1fdfc4a7b52bb28496a29f6cc0a16605
kustomize build ./user-configuration/development
```