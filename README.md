# Traeffik
Installing cert-manager
First, let’s install the CRDs:

kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v0.15.2/cert-manager.crds.yaml

Now let’s create the namespace, add the Helm repository and install it:

kubectl create namespace cert-manager
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install cert-manager jetstack/cert-manager --namespace cert-manager --version v0.15.2

To check if the installation succeeded you can check if the pods are running:

kubectl get pods --namespace cert-manager

Configure your DNS provider to point to your Traefik service
I’m going to use the domain secure.alexguedes.com for this exercise, but you’ll need to configure your DNS provider to point this domain to the IP address of the LoadBalancer created by Traefik.

You can see the IP address of the LoadBalancer created with the following command:

kubectl -n traefik get svc
Deploy a website with Nginx

https://medium.com/@alexgued3s/how-to-easily-ish-471307f276a9
