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

