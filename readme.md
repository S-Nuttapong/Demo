# Traffy_Demo

### serving object detection model for sanitation and public infrastructure with `tensorflow-serving`

## Installation

The installation process is thoroughly described in the [docs/setup.md](docs/setup.md). 
In prior being able to serve a `Traffy Demo` with tensorflow-serving.

## Serving traffy_demo with tensorflow/serving image

follow: [docs/tf_server_local.md](docs/tf_server_local.md).

## Serving with kubenetes (pulled from traffy_demo container from Google Cloud's registry)

follow: [docs/tf_server_k8s.md](docs/tf_server_k8s.md).

### Credits

The `object_detection` directory comes from the
[tensorflow-model](https://github.com/tensorflow/models) repository. 
It offers useful `utils` functions to tag the image returned from the model.

Tutorial: https://towardsdatascience.com/deploy-your-machine-learning-models-with-tensorflow-serving-and-kubernetes-9d9e78e569db

