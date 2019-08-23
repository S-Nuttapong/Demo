# Traffy_Demo

### serving object detection model for public sanitation and infrastructure problems with `tensorflow-serving`

## Required Installation

Follow [docs/setup.md](docs/setup.md) to run TensorFlow-serving client.

## Serving on localhost

Follow: [docs/tf_server_local.md](docs/tf_server_local.md).

## Serving with Kubenetes (hosted on GCE's registry)
follow: [docs/tf_server_k8s.md](docs/tf_server_k8s.md).

### Credits

The `object_detection` directory comes from the
[tensorflow-model](https://github.com/tensorflow/models) repository. 
It offers useful `utils` functions to tag the image returned from the model.

Tutorial: https://towardsdatascience.com/deploy-your-machine-learning-models-with-tensorflow-serving-and-kubernetes-9d9e78e569db

Original Repository: https://github.com/fpaupier/tensorflow-serving_sidecar
