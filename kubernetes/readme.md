
# VMWare exporter on Kubernetes

First edit the vmware-exporter-configmap.yaml file to match your setup.
Afterwards, using the read command interactively type in your password, 
then run the command to create your secret on the cluster.
And finally deploy the exporter container.

The pod has prometheus annotations so when there's a prometheus on the cluster it will auto scrape the pod.

```
read -s VSPHERE_PASSWORD
kubectl create secret generic vmware-exporter-password --from-literal=VSPHERE_PASSWORD=$VSPHERE_PASSWORD
kubectl apply -f vmware-exporter-configmap.yaml
kubectl apply -f vmware-exporter-deployment.yaml
```
