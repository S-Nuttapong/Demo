# Project setup

Setup a working python environment

## Create a Python virtualenv

**Note** This project runs on Python 3.6.5
Download Python 3.6.5:  https://www.python.org/downloads/release/python-365/

Create a python virtual environment with venv, name it as you wish, for example ```tf_serving``` Replace the path /PATH/TO to your desired virtualenv accordingly, for example ```virpython``` .
```
pip3 install virtualenv

mkdir virpython <<<< </PATH/TO>

cd ~/virpython

virtualenv -p python3.6 tf_serving <<<<<<<< <VENV NAME>
```
Activate Virtual environment
```
source ~/virpython/tf_serving/bin/activate
```

## Install all dependencies
Install the python packages required for the project. Run the following at the root of the project directory:
```
cd /PATH/TO/Traffy_Demo

# From Traffy_Demo/
pip install -r requirements.txt
``` 

## Install Protobuf
The Tensorflow `Object Detection` API uses Protobufs to configure model and training parameters. 
Before the framework can be used, the Protobuf libraries must be compiled. 
 
Follow the instruction in **Protobuf Compilation** section of official tensorflow installation guide:  https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md 

### Protobuf Compilation

Once the installation is complete you can compile the protobufer libraries of the project with `protoc`, 
it should be done by running the following command from the root directory of this project:
```bash
# From tensorflow-serving_sidecar
protoc object_detection/protos/*.proto --python_out=.
```
## Next

### Serving traffy_demo with tensorflow/serving image on localhost

follow: [docs/tf_server_local.md](docs/tf_server_local.md).

### Serving with kubenetes (pulled from traffy_demo container from Google Cloud's registry)

follow: [docs/tf_server_k8s.md](docs/tf_server_k8s.md).

