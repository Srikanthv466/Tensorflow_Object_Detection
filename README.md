
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

Open inferency.ipynb and run all the cells one by one.


## Model Training

Convert COCO annotations into Pascal VOC format, and we should build TFRecords from the Pascal VOC annotations.

Create label_map.pbtxt

Make necessary changes in the pipeline.config files.

Run the below command in the anaconda prompt

```bash
python model_main_tf2.py --model_dir=path_to_model_outputs --pipeline_config_path=path_to_pipeline.config
```

