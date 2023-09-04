# Using the bitnami Wordpress helm chart

## Value file
For OpenShift we need to disable any specific userid hardcoded to 1001. Instead we remove runAsuser and FSGroup settings by disabling the securityContext features in the values.yanl file and let OpenShift choose the user/group.

## Install helm

helm install <install name> oci://registry-1.docker.io/bitnamicharts/wordpress -f values.yaml

## Expose Route
For insecure oc expose svc/<install name>
For secure oc create route edge wordpress --service=<install name> --port=80 --insecure-policy=Redirect  
