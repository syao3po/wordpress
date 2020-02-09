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
</pre>

# Step 2
<pre>
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/kustomization.yaml
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/mysql-deployment.yaml
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/wordpress-deployment.yaml
</pre>
# Step 3
<pre>
# kubectl apply -k ./
secret/mysql-pass-bc925kcfmd created
service/wordpress-mysql created
service/wordpress created
deployment.apps/wordpress-mysql created
deployment.apps/wordpress created
persistentvolumeclaim/mysql-pv-claim created
</pre>
