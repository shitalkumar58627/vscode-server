READme.md

for this deploy we have created a secre named as code-server-secret and we have passed this to kubernete cluster 
to do this we have used below commnads

##########################

 to create secret
         

[         Actul password of application]                            [name of secrete ]
 echo -n '0215f4f761a368202b93d3a6' | kubectl create secret generic code-server-secret --from-literal=password=$(base64 -w0)

 using above command we have created secret with the name of code-server-secret 


 #################################

 how to decrypt this secret  now 
 using below command we can decrypt the secret as below


 kubectl get secret code-server-secret -o jsonpath='{.data.password}' | base64 --decode


READme.md

for this deploy we have created a secre named as code-server-secret and we have passed this to kubernete cluster 
to do this we have used below commnads

##########################

 to create secret
         

[         Actual password of application]                            [name of secrete ]
 echo -n '0215f4f761a368202b93d3a6' | kubectl create secret generic code-server-secret --from-literal=password=$(base64 -w0)

 using above command we have created secret with the name of code-server-secret 


 #################################

 how to decrypt this secret  now 
 using below command we can decrypt the secret as below


 kubectl get secret code-server-secret -o jsonpath='{.data.password}' | base64 --decode



====================================================================


how to deploy this app on argocd 
First, create a new namespace for ArgoCD:

kubectl create namespace argocd
Next, install the ArgoCD server by applying the following manifest:

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
This manifest will create the necessary Kubernetes resources to run the ArgoCD server.

Verify that the ArgoCD server is running by checking the status of the argocd-server deployment:

kubectl -n argocd get deployment argocd-server
The output should show that the deployment has one or more replicas and that all replicas are ready.

To access the ArgoCD server, create a port-forward to the server's service:

kubectl port-forward svc/argocd-server -n argocd 8080:443
This will allow you to access the ArgoCD server's web UI at https://localhost:8080 in your local browser.

By default, the ArgoCD server is secured with a default username and password. To retrieve the password, run the following command:

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
This will decode the password from base64 encoding. You can use this password to log in to the ArgoCD server's web UI.
