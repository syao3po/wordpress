# wordpress

Please make folder, and Download 3 files at same folder.

folder
|
|----kustomization.yaml
|----mysql-deployment.yaml
|----wordpress-deployment.yaml

---------

# Step 1
# mkdir folder ; cd folder

# Step 2
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/kustomization.yaml
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/mysql-deployment.yaml
# curl -LO https://raw.githubusercontent.com/syao3po/wordpress/master/wordpress-deployment.yaml

# Step 3
# kubectl apply -k ./
