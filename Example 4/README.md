Kustomization also allows to dynamically create and add secrets for the resources/workloads without embedding the secrets with workloads' file first. 

To do this, kustomization.yml contains a tag "secretGenerator" which takes either the file of the secret or the secret credentials in a literal manner. While attaching the secret file, we have to mention the path and name of the file to the "files" field in the "secretGenerator" tag. While using the literal method, the literals are mentioned inside the 'kustomization.yml' file and these are dynamically added to the attached workload. The workload file name is mentioned in the "resources" tag.

Workflow;
1. "kubectl apply -k ." applies the kustomization and deploys the workload.
2. Now for the secrets, it first converts the secrets into alphanumeric code and then stores it inside the dynamically created secret file    that is being attached to the workload. It means that the information of secret is first encrypted into the alphanumeric code and then    decrypted while being attached to the workload.

The newly generated secret file when attaching the already present secret file (password.txt) can be as follows:

apiVersion: v1
data:
  password.txt: dXNlcm5hbWU9YWRtaW4KcGFzc3dvcmQ9c2VjcmV0Cg==
kind: Secret
metadata:
  name: example-secret-1-t2kt65hgtb
type: Opaque

The newly generated secret file when using the literals in the "kustomization.yml" can be as follows:

apiVersion: v1
data:
  password: c2VjcmV0
  username: YWRtaW4=
kind: Secret
metadata:
  name: example-secret-2-t52t6g96d8
type: Opaque

Everytime we attach a new secret file or use a new literal in the "kustomization.yml", a new secret file is created and attached to the workload. This is done avoid conflicts in building and working of the workload. Also, when the new secret file is made and attached to the workload, the .yml file of the workload also changes its reference to the new secret file. Check 'kubectl get secrets' for all the newly made secrets.
