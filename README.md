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
- [x] Your Custom Dataset `(Google Drive)`
- [x] Google Colab
## HOW TO SET-UP:
**Import Your Google Drive**
> Be sure that you are using the same Google Account on the Google Colab notebook and the Google Drive where you have your dataset
#### Code Sinppets:
```
from google.colab import drive
drive.mount('/content/drive')```
