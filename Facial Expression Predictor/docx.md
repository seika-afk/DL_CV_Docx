https://github.com/seika-afk/Facial-Expression-Detector/blob/main/model.ipynb

Introduction : As stated in title
- Training a cnn model for predicting human Emotions 


## Data Extraction

1. Download the dataset , from kaggle 
also before downloading , you need to provide your api key, you can check the initial cells for that


There are usually different methods for using the images as data for tensorflow pipeline , 
one is to have a folder like this

/folder
	/subfolder1
	/subfolder2
where subfolders are just different predictable entities,

there are other methods like , putting their location into a csv format , along with the entity 
and many more that we will discuss later

Then extract the data like normally using zipfile ,if you are in collab

and convert the images available in  tensorflow format , by the following command :




```

train_dataset= keras.utils.image_dataset_from_directory(
	director='./images/train'
	labels='inferred'
	label_mode='int'

..bactch size and image size

)

```

create validation dataset


now that we have vectors, normalize them to a range in between 0 to 1 .


Process the image -> Cast them into float



Before this step , you could perform , EDA on the data too 


# Model 


Here our model is sequential :layers stacked on top of each other


functional -> if more output is needed


```
- INPUT LAYER
- CONV2D -32
- Batchnormalization 
  ...
  ...
  ...
  Flatten these spatial dimensional ds
  Add nns
  with dropouts


```


i have written sometimes some non sensical comments , so do ignore them 



# Model Training 

```
use Adam , for optimization of model parameters

then compile it -> use proper loss


```


Accuracy is a lot low , this is because of lack of enough training , cnns requires a lot of training time , so do keep that in mind and we could apply some of these techniques

Data augmentation
Transfer learning
More dropout
Regulization
Hyperparameter tuning
