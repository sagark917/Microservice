kubectl create namespace webapps
kubectl apply -f svc.yml
kubectl apply -f role.yml
kubectl apply -f bind.yml
kubectl apply -f sec.yml -n webapps
# To get the secret key
kubectl -n webapps describe secret mysecretname
sudo chmod 666 /var/run/docker.sock

#To delete eks cluster
kubectl delete cluster --name EKS-1 --regoin ap-south-1
