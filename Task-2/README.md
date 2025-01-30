# Two Pin and Three PIn PLug Detector using YOLOv5

This project demonstrates how to train a custom YOLOv5 model to detect 2-pin and 3-pin plugs. The notebook guides you through the entire process, from dataset preparation to model training and evaluation.

#### Key insights:

- Dataset size: 52
- Dataset ratio:
  - Train: 36
  - Valid: 11
  - Test: 5
- [Download Dataset](https://app.roboflow.com/ds/Q3xrNRucK2?key=8TBgZwizkG)

## Table of Contents

- [Introduction](#introduction)
- [Steps](#steps)
  - [Step 1: Install Requirements](#step-1-install-requirements)
  - [Step 2: Assemble the Dataset](#step-2-assemble-the-dataset)
  - [Step 3: Train the Custom YOLOv5 Model](#step-3-train-the-custom-yolov5-model)
  - [Step 4: Evaluate the Model](#step-4-evaluate-the-model)
  - [Step 5: Run Test Inference](#step-5-run-test-inference)
- [Sample Results](#sample-results)
- [Conclusion](#conclusion)

## Introduction

In this tutorial, we assemble a dataset and train a custom YOLOv5 model to recognize 2-pin and 3-pin plugs. The steps include gathering and labeling a dataset, training the model, evaluating its performance, and running test inferences.

## Steps

### Step 1: Install Requirements

First, we need to clone the YOLOv5 repository and install the necessary dependencies.

```python
# Clone YOLOv5 and install dependencies
!git clone https://github.com/ultralytics/yolov5  # clone repo
%cd yolov5
%pip install -qr requirements.txt  # install dependencies
%pip install -q roboflow

import torch
import os
from IPython.display import Image, clear_output  # to display images

print(f"Setup complete. Using torch {torch.__version__} ({torch.cuda.get_device_properties(0).name if torch.cuda.is_available() else 'CPU'})")
```

### Step 2: Assemble the Dataset

We need to assemble a dataset of images with bounding box annotations around the yellow markers. This dataset should be in YOLOv5 format.

```python
!pip install roboflow

from roboflow import Roboflow
rf = Roboflow(api_key="YOUR_API_KEY")
project = rf.workspace("YOUR_WORKSPACE").project("YOUR_PROJECT")
version = project.version(4)
dataset = version.download("yolov5")
```

### Step 3: Train the Custom YOLOv5 Model

We train the YOLOv5 model using the assembled dataset. Various parameters such as image size, batch size, number of epochs, and weights for transfer learning can be specified.

```python
!python train.py --img 640 --batch 16 --epochs 70 --data {dataset.location}/data.yaml --weights yolov5s.pt --cache
```

### Step 4: Evaluate the Model

After training, we evaluate the model's performance on the validation dataset.

```python
!python val.py --data {dataset.location}/data.yaml --weights runs/train/exp/weights/best.pt --img 640
```

### Step 5: Run Test Inference

Finally, we run test inferences to see the model in action.

```python
!python detect.py --weights runs/train/exp/weights/best.pt --img 640 --conf 0.25 --source {dataset.location}/test/images
```

## Sample Results

![](./Images/1.jpeg)
![](./Images/2.jpeg)
![](./Images/3.jpeg)
![](./Images/4.jpeg)
![](./Images/5.jpeg)
![](./Images/6.jpeg)

## Conclusion

This project demonstrates the process of training a custom YOLOv5 model to detect 2-pin and 3-pin plugs. By following the steps outlined in the notebook, you can train your own object detection model for any custom dataset.

For more details, please refer to the notebook.

## Acknowledgements

- [Notebook Reference](https://colab.research.google.com/drive/1Cc8KGyrey9oCyRh4h7CNnadD_gwr0PA8?usp=sharing)
- [RoboFlow](https://roboflow.com/)
