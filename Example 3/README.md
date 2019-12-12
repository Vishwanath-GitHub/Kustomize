Kustomization also allows to dynamically create config-files i.e. config-maps for the resources/workloads without creating the workloads' config file first.

To do this, kustomization.yml contains a tag "configMapGenerator" which takes the name of the workload and the config file (.conf). This '.conf' file contains the parameters that can both be changed manually and by the kustomization automatically. This tag generates the config files dynamically and also makes changes to it. The workload file name is mentioned in the "resources" tag.

Workflow:
1. "kubectl apply -k ." applies the kustomization and deploys the workload. It also makes the config file for the workload at the same time.
2. Whenever we change some parameters in the 'nginx.conf' file and use "kubectl apply -k ." again, a new config file is made for the workload and it is now deployed. Making a new config file and applying it to the workload doesn't stop the running workload.

For example, we can change "worker_process 1;" to "worker_process 3;" and use "kubectl apply -k .", it creates new config file with the new configuration and applies it to the running workload. Check 'kubectl get configmaps' for this.

The concept of making new config file everytime for a change is used to avoid conflicts in the building and working of the workload. Also, when the new config file is made and attached to the workload, the .yml file of the workload also changes its reference to the new config file.
