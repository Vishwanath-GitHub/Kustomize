Using Kustomize in the same directory where all the supporting files exist:
1. In your Kubernetes, make a folder named as 'base'
2. Copy all the files from the 'base' folder of this Git repository to your newly made 'base' folder.
3. Use this command in that folder: "kubectl apply -k ."

Using Kustomize where all files are not in the same directory:
(this can also be used to change some properties of the actual .yml files like we are changing the version of the base image here)
(it is actually using files from the 'base' directory despite being in the 'overlays' directory)
1. In your Kubernetes, make a new folder named as 'overlays'.
2. Copy all the files and folder from the 'overlays' folder of this Git repository to your newly made 'overlays' folder.
   (Don't copy the README.md file)
3. Create a new namespace named as 'prod'.
4. Use this command in the 'prod' folder: "kubectl apply -k ."
