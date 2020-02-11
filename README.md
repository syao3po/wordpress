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
1) Install go
https://github.com/astaxie/build-web-application-with-golang/blob/master/ja/01.1.md

<pre>
# tar -C /usr/local/src -xzf go1.8.darwin-amd64.tar.gz
# echo 'export GOROOT="/usr/local/src/go"' >> ~/.bash_profile
# echo 'export PATH="$GOROOT/bin:$PATH"' >> ~/.bash_profile
# source /etc/profile
</pre>
2) Ingress Controller Install
https://github.com/jcmoraisjr/haproxy-ingress
<pre>
mkdir -p $GOPATH/src/github.com/jcmoraisjr
cd $GOPATH/src/github.com/jcmoraisjr
git clone https://github.com/jcmoraisjr/haproxy-ingress.git
cd haproxy-ingress
make
</pre>

# Step 5

Create Ingress

<pre>
# HOST=`hostname`
# kubectl -n wordpress create -f - << EOF
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
        path: /wordpress
EOF
</pre>


