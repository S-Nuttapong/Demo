# Serving traffy_demo with tensorflow/serving image on localhost

Finalize your setup by running your first tensorflow-server on local.
You will be able to make object detection over `jpeg` images in a few minutes!

## First, get TensorFlow-serving image
Run: `docker pull tensorflow/serving`

Then do the following:

1. Run the tensorflow server container:
```bash
# From Traffy_Demo/
docker run -t --rm -p 8501:8501 \
   -v "$(pwd)/data/$faster_rcnn_road:/models/faster_rcnn_road" \
   -e MODEL_NAME=faster_rcnn_road \
   tensorflow/serving &
```

2. Run client.py, tensorflow-serving client: 
```bash
# Don't forget to activate your python3.6.5 venv

# From Traffy_Demo/
python client.py --server_url "http://localhost:8501/v1/models/faster_rcnn_road:predict" \
--image_path "$(pwd)/Test/road/pit29.jpg" \
--output_json "$(pwd)/Test_Result/pit29.json" \
--save_output_image "True" \
--label_map "$(pwd)/data/faster_rcnn_road/label_map.pbtxt"
```
Note: other images can be find at `Traffy_Demo/Test/Images/`

If everything works fine you should have an image generated under `Test_Result/pit29.jpeg`.
With the provided model and example it should look like:
![Output image based on the inference results from the model](../assets/pit29.jpeg) 
