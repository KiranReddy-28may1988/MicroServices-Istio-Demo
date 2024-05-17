# MicroServices-Istio-Demo
Sample micro services app with Istio capabilities like service mesh, Grafana, prometheus,jaeger and Kiali.

# pre-requistites:
If you are doing it on local machine make sure you have either minikube or Docker-Desktop instlled

# Exporting the path of Istioctl:
export PATH=./istio-1.22.0/bin:$PATH
verify if the path is exported correctly or not by running the following command:

istioctl version

# Install Istio components on kubernetes cluster

istioctl install 

Istio components will get installed on Istio-system namespace,to verify run the below commands:

kubectl get pods -n istio-system

# Installing the application by running the kubernetes manifest file:

By defualt the application will install at the default name space but in my scenarion i would like to install it on dedicated namespace so i'm creating a namespace called shopping-app

kc create namespace shopping-app

# Label the namespace istio-injection=enabled  for configuring the envoy 

kubectl get namespace --show-labels   ===> This will list the namespace with existing labels. 

kubectl label namespace shopping-app istio-injection=enabled --overwrite   ===> This will label the name namespace as <  istio-injection=enabled,kubernetes.io/metadata.name=shopping-app >

# switch to the shopping-app as defualt namespace 

kubectl config set-context --current --namespace shopping-app

