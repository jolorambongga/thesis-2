# MOTORCYCLE HELMET DETECTION 
## Table of Contents:
- [Train Model (For Rider)](#modelRider)
- [Train Model (For Helmet](#modelHelmet)
- [Train Model (For Plate)](#modelPlate)
<a name="modelRider" />

##### TRAIN THE MODEL FOR RIDER DETECTION
- The ``"train-model-rider"`` is used for training the YOLOv5 model with pre-trained weights using a custom dataset uploaded on google-drive.
<a href="https://colab.research.google.com/drive/1O6OGddenAvl-OzJ7Q9wkIfNKcrZYHdHr#scrollTo=ezm9utIa5Sof" target="_blank">Link forthe training model using Google Colab</a>
<a name="modelHelmet" />

##### TRAIN THE MODEL FOR HELMET DETECTION
- The `"train-model-helmet"` is used for training the YOLOv5 model with pre-trained weights using a custom dataset from roboflow uploaded on google-drive.
<a href="#" targe="_blank">Link for the training model using Google Colab</a>
<a name="modelPlate" />

##### TRAIN THE MODEL FOR PLATE DETECTION
- The `"train-model-plate"` is used for training the YOLOv5 model using custom dataset from roboflow uploaded on google-drive.
<a href="#" targe="_blank">Link for the training model using Google Colab</a>
<a name="" />

#### BEFORE SET-UP (PREPARE THE FOLLOWING):
- [x] Your Custom Dataset in Google Drive `(I recommend having 1k images total, then follow the guide I provided below for organizing your dataset)`
- [x] Google Colab
***
## HOW TO SET-UP:
**Import Your Google Drive**
> Be sure that you are using the same Google Account on the Google Colab notebook and the Google Drive where you have your dataset
> Be sure to use the yolov5 format for the dataset `(your folder should contain the following folders)`
```
└── images
  ├── train
  ├── validate
  ├── test
└── labels
  ├── train
  ├── validate
  ├── test
```
> **Note**: you may check the YOLOv5 documentary for training <a href="https://docs.ultralytics.com/yolov5/tutorials/train_custom_data/">here</a>.
>> **Additional Note**: you may change the folder names for `train, validate, and test` however, the folders: **"images"** and **"labels"** should remain the same. This is how yolov5 locates your iamges and labels therefore, you **SHOULD NOT** change it!
>>> **Even More Note**: the `train` folder inside images/labels folder; should contain all the necessary images/labels for detection *(I would recommend about 80% of your total photos gathered --so if you have 1k photos, that would be 800 photos for the train folder)*: more images = more accurate.
>>> the `validate` folder should contain about `10% of total data`
#### Code Sinppets and Set-up:

##### Import Google Drive:
```
from google.colab import drive
drive.mount('/content/drive')
```
<a name="checkDir"/>

##### Check for current Directory:
> Be sure that your current directory is inside your Google Drive; so that when you git clone the YOLOv5 repository, it will be saved inside your drive.
```
!pwd
```
<a name="changeDir"/>

##### Change the current Directory:
```
%cd /content/drive/MyDrive/path/to/your/desired/folder
```
##### GIT Clone the YOLOv5 Repository:
```
!git clone https://github.com/ultralytics/yolov5  # clone
%cd yolov5
%pip install -qr requirements.txt comet_ml  # install

import torch
import utils
display = utils.notebook_init()  # checks
```
##### Create your own `customData.yaml` file:
> Go to the YOLOv5 folder path in your google drive, right click the data folder inside yolov5 folder and click "create new file" and name it "customData.yaml" (or any desired file name) `see the folder branch below for guide
```
└── content
  └── drive
    └── myDrive
      └── yolov5
        └── data
```
###### Example of my own `customData.yaml` file: `(the classes may vary depending on your dataset; however, this is the format you should follow)`
```
train: /content/drive/MyDrive/path/to/dataset/train/images
val: /content/drive/MyDrive/path/to/dataset/validate/images
test: /content/drive/MyDrive/path/to/dataset/test/images

# Classes
names:
  0: rider
  1: not_rider
  2: with_helmet
  3: without_helmet
  4: plate_num
```
##### Train the model with your own `customData.yaml`: **before running, make sure that you are inside the yolov5 folder*
> Use the code snippet to [check for current directory](#checkDir) and the code snippet to [change the directory](#changeDir)
```
!python train.py --img 640 --batch 16 --epochs 100 --data myData.yaml --weights yolov5x.pt
```
