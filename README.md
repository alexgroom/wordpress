# Using the bitnami Wordpress helm chart

## Value file
For OpenShift we need to set user and group id so that it is NOT hardcoded to 1001. Remove runAsuser and FSGroup settings by choosing the supplied value.yaml file

## Install helm

helm install <install name> oci://registry-1.docker.io/bitnamicharts/wordpress -f values.yaml

## Expose Route
For insecure oc expose svc/<install name>
For secure oc create route edge wordpress --service=<install name> --port=80 --insecure-policy=Redirect  
