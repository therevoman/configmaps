While trying to understand the inner workings of OpenShift 3.5 I put together this demo of config maps.  
This is a very simple setup and uses the docker.io/busybox image for simplicity.
A ConfigMap is created from a directory containing multiple property files.
Then a Pod is created that references that ConfigMap as a VolumeMount

Here are the steps to recreate
# Busybox configmap example
## create configmap
oc create configmap test-configmap --from-file=properties/

## delete and create pod
oc delete -f config-map-pod.yml; oc create -f config-map-pod.yml

## look at logs when pod has exited
oc logs dapi-test-pod

# httpd configmap example
## create configmap
oc create configmap special-config --from-file=httpdfiles/

## delete pod
oc delete -f httpd-pod.yml

## create pod
oc create -f httpd-pod.yml

## look at logs when pod has exited
oc logs dapi-test-pod
