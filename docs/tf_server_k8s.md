# Serving with Kubenetes (pulled from traffy_demo container from Google Cloud's registry)

Run the following command
 ````bash
# From tensorflow-serving_sidecar/
kubectl create -f faster_rcnn_resnet_k8s.yaml
````
To view status of the deployment and pods use the `kubectl get deployments` for the whole deployment, `kubectl get pods`
to monitor each replicas of your deployment and `kubectl get services` for the service.

![monitor deployment kube](../assets/kube_deployment.png)


It can take a while for everything to be up and running. The service external `IP` address is listed next to LoadBalancer Ingress.
You can check it with the ``kubectl describe service`` command:
````bash
kubectl describe service faster-rcnn-resnet-service
````
![monitor service](../assets/service_description.png)

## Query your online model

And finally, let's test this. We can use the same [client code](../client.py).
Simply replace the previously used ``localhost`` in the url with the `IP` address of the LoadBalancer.

````bash
# From tensorflow-serving_sidecar/
python client.py --server_url "http://34.73.137.228:8501/v1/models/faster_rcnn_resnet:predict" \
--image_path "$(pwd)/object_detection/test_images/image1.jpg" \
--output_json "$(pwd)/object_detection/test_images/out_image3.json" \
--save_output_image "True" \
--label_map "$(pwd)/data/labels.pbtxt"
````
________
### Resources 


- More resources on Docker `bind` mount is available on [Docker bind official docs](https://docs.docker.com/storage/bind-mounts/).
- To understand how the docker `commit` command works, refer to the [Docker commit official doc](https://docs.docker.com/engine/reference/commandline/commit/).
- Google Container registry documentation, https://cloud.google.com/container-registry/docs/
