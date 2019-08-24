# Project setup

Setup a working python environment

## Create a Python virtualenv

**Note** This project runs on Python 3.6.5
Download Python 3.6.5:  https://www.python.org/downloads/release/python-365/

### For windows
follow: https://programwithus.com/learn-to-code/Pip-and-virtualenv-on-Windows/

### For mac

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

### Clone This Repository 

### Download demo model and put inside data folder
Model can be found here: https://drive.google.com/open?id=1BjW7LQ-2KC-74anW0u5iJu8mXEys0w7U
and put model inside data folder as shown below:
```
Traffy_Demo/
 |
 |--data/
 |     |
 |     |--faster_rcnn_road/
 |             |
 |             |-label_map.pbtxt
 |             |
 |             |--00001/
 |                |
 |                |-saved_model.pb 
 |                |
 |                |-variables/
 |             
 |     
 |
 |--docs/
 |
```
### Install the python packages required for the project. Run the following at the root of the project directory:
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

### Serving on local host

follow: [tf_server_local.md](tf_server_local.md).

### Serving with kubenetes (hosted on GCE's registry)

follow: [tf_server_k8s.md](tf_server_k8s.md).

