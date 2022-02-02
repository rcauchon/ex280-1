```
oc new-project q1
oc create configmap index --from-file=./index.html 
oc new-app --name bnginx --image=bitnami/nginx 
oc set env deployment/bnginx --from=configmap/index
oc set volume deployment/bnginx --add --name config-volume --type configmap --configmap-name=index --mount-path=/app
```

```
oc apply -f bnginx.yaml
oc expose service bnginx
curl http://bnginx-q1.apps-crc.testing
```
