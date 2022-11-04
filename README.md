# k8s-test

It's a DIY kind of tech assessment, as long as you can demonstrate your skills in Kubernetes. 

I got the app already packaged in a Docker image, see Dockerfile. 

The application is deployed in a Kubernetes cluster with HPA (auto-scaling) enabled. 
The point of entry for traffic is via an Ingess.

I've also use Helm chart for this assessment (easier to re-use in the future!)

Dependencies:
- AKS cluster, of course.
- install helm and kubectl.

Deployment instructions:
1. Install the Helm chart
```
helm upgrade --install mytest mytest-chart
```
2. Install the Nginx controller and the ingress. 
```
helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace ingress-nginx --create-namespace
kubectl apply -f ingress.yaml
```

Verify that it's working:
``
kubectl get ingress -A
```
You should see a public IP assigned. 
Now access the IP with the prefix/path as per Ingress manifest. (eg. http://1.1.1.1/web ) 


