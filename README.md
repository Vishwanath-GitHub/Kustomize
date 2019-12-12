Kustomize is built-in tool for Kubernetes that is used to perform some changes in the .yml file of the workloads automatically. It is a template-free .yml developer tool for multiple purposes like patching, config-file generation, adding secrets etc.

- Kustomize allows to store multiple configuration per Git repository.
- It is built-in with kubectl v1.14+ and can be accessed with '-k' or '--kustomize'

The default normally used command for Kustomization via 'kubectl' are;
1. "kubectl apply -k ." //Used to apply the Kustomization
2. "kubectl get -k ." //Used to get all the workloads deployed by the Kustomization and the changes made to it(similar to kubectl get all)
3. "kubectl describe -k ." //Used to get all the details of the workloads deployed by the Kustomization and the changes made to it(similar to kubectl describe all)
4. "kubectl delete -k ." //Used to delete all the workloads deployed by the Kustomization and the additional changes made with it (similare to kubectl delete all)

The file-structure comprises of 'base' folder and 'overlays' folder. This arrangement makes it easy to manage your configuration with git. The base could have files from an upstream repository managed by someone else. The overlays could be in a repository you own.
Check the examples for its working and usage.

Go to this link to know what features Kustomize provides:- https://kubernetes.io/docs/tasks/manage-kubernetes-objects/kustomization/#kustomize-feature-list
