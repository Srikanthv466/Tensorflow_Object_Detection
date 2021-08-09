
# Object detection

The goal is to classify and localize Person and Car objects in the images.


## Run Inference

Clone the project

```bash
  git clone https://github.com/Srikanthv466/Tensorflow_Object_Detection.git
```

Go to the project directory

```bash
  cd Tensorflow_Object_Detection
```
Create a virtual environment in anaconda prompt

```bash
  conda create -n <virtual_environment_name> python=3.6
```
Activate virtual environment

```bash
  conda activate <virtual_environment_name>
```

Install dependencies

```bash
  pip install requirements.txt
```

Installing Tensorflow object detection API

```bash
git clone 'https://github.com/tensorflow/models.git'
```

Open inferency.ipynb and run all the cells one by one.


## Model Training

Convert COCO annotations into Pascal VOC format, and then build TFRecords from the Pascal VOC annotations using generate_tfrecord.py file.

Create label_map.pbtxt

Download any pre-trained model from tensorflow models zoo.

Make necessary changes in the pipeline.config file like path to pre-trained model checkpoint, label_map.pbtxt. train.record, test.record etc..

Clone the TensorFlow Models repository and proceed to one of the installation options.

```bash
  git clone 'https://github.com/tensorflow/models.git'
```

Installing object detection API and compiling proto files.

```bash
  cd models/research
  # Compile protos.
  protoc object_detection/protos/*.proto --python_out=.
  # Install TensorFlow Object Detection API.
  cp object_detection/packages/tf2/setup.py .
  python -m pip install --use-feature=2020-resolver .
```

A local training job can be run with the following command:

```bash
# From the tensorflow/models/research/ directory
PIPELINE_CONFIG_PATH={path to pipeline config file}
MODEL_DIR={path to model directory}
python object_detection/model_main_tf2.py \
    --pipeline_config_path=${PIPELINE_CONFIG_PATH} \
    --model_dir=${MODEL_DIR} \
    --alsologtostderr
```
where ${PIPELINE_CONFIG_PATH} points to the pipeline config and ${MODEL_DIR} points to the directory in which training checkpoints and events will be written.

A local evaluation job can be run with the following command:

```bash
# From the tensorflow/models/research/ directory
PIPELINE_CONFIG_PATH={path to pipeline config file}
MODEL_DIR={path to model directory}
CHECKPOINT_DIR=${MODEL_DIR}
MODEL_DIR={path to model directory}
python object_detection/model_main_tf2.py \
    --pipeline_config_path=${PIPELINE_CONFIG_PATH} \
    --model_dir=${MODEL_DIR} \
    --checkpoint_dir=${CHECKPOINT_DIR} \
    --alsologtostderr
```
where ${CHECKPOINT_DIR} points to the directory with checkpoints produced by the training job. Evaluation events are written to ${MODEL_DIR/eval}

