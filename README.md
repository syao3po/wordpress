# wordpress

Please make folder, and Download 3 files at same folder.
<pre>
folder
|
|----kustomization.yaml
|----mysql-deployment.yaml
|----wordpress-deployment.yaml
</pre>
---------

# Step 1
<pre>
# mkdir folder ; cd folder
# kubectl create ns wordpress
</pre>

# Step 2
<pre>
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/kustomization.yaml
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/mysql-deployment.yaml
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/wordpress-deployment.yaml
</pre>
# Step 3
<pre>
# kubectl -n wordpress apply -k ./
secret/mysql-pass-bc925kcfmd created
service/wordpress-mysql created
service/wordpress created
deployment.apps/wordpress-mysql created
deployment.apps/wordpress created
persistentvolumeclaim/mysql-pv-claim created
</pre>

# Step 4
Ingress Controller Install



# Step 5
<pre>
Create Ingress
# kubectl delete -f - <<EOF
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: wordpress
spec:
  rules:
  - host: $HOST
    http:
      paths:
      - backend:
          serviceName: wordpress
          servicePort: 80
        path: /
EOF
</pre>
