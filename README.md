Kustomize is built-in tool for Kubernetes that is used to perform some changes in the .yml file of the workloads automatically. It is a template-free .yml developer tool for multiple purposes like patching, config-file generation, adding secrets etc.

- Kustomize allows to store multiple configuration per Git repository.
- It is built-in with kubectl v1.14+ and can be accessed with '-k' or '--kustomize'

The file-structure comprises of 'base' folder and 'overlays' folder. This arrangement makes it easy to manage your configuration with git. The base could have files from an upstream repository managed by someone else. The overlays could be in a repository you own.
Check the examples for its working and usage.

Go to this link to know what features Kustomize provides:- https://kubernetes.io/docs/tasks/manage-kubernetes-objects/kustomization/#kustomize-feature-list
