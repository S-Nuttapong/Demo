# Serving with Kubenetes (hosted on GCE's registry)

Run the following command
 ````bash
# From tensorflow-serving_sidecar/
kubectl create -f faster_rcnn_road_k8s.yaml
````
To view status of the deployment and pods use the `kubectl get deployments` for the whole deployment, `kubectl get pods`
to monitor each replicas of your deployment and `kubectl get services` for the service.

![monitor deployment kube](../assets/kube_deployment.png)


It can take a while for everything to be up and running. The service external `IP` address is listed next to LoadBalancer Ingress.
You can check it with the ``kubectl describe service`` command:
````bash
kubectl describe service faster-rcnn-traffy-service
````
![monitor service](../assets/service_description.png)

## Query your online model

And finally, let's test this. We can use the same [client code](../client.py).
Simply replace the previously used ``localhost`` in the url with the `IP` address of the LoadBalancer.

````bash
# From Traffy_Demo/
python Client_Kube.py --save_output_image "True" 

````

