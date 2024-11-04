
# Manifest Hydration

To hydrate the manifests in this repository, run the following commands:

```shell

git clone https://github.com/crenshaw-dev/argocon-gitops-promoter-hydrate-demo
# cd into the cloned directory
git checkout 9b95de9c1f13c4993c343db8628cb602e99b6978
kustomize build ./user-configuration/production/us-east-2
```