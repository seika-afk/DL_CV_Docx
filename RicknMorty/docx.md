Since i love rick and morty so much  , i decideed to create a cnn model for it too


# Data preparation :
The same procedure-> install from the kaggle and extract it


Since we did too much on "from directory " method , this time we are doing ,something different , saving the image location inside a csv 
and utilizing it


1. First we iterate over the folder ,and all its subfolders ,then to its images , and add the image_path in array ,for each and just like that , to the label too
make sure they are concurrent to each other

2. Then make data using these two arrays , then convert to datafram
and save it 


same for test dataset


# Now augmentation :
basically making more dataset by rotating ,cropping etc to our existing data

first split the data into train and val , 

then Use ImageDataGenerator function to augment data


#### Final step for data preparation :

now create train_generator from our csv 
btw train_generator wil be generator object , used to generate batches of images


# EDA 

- check shape 
- info
- describe
- label distribution -> count plot for each feature
- pie chart too


# Model Building 


```
model=Sequential()

model.add(Input(shape=(224,224,3)))

model.add(Conv2D(64,(5,5),activation='relu'))
model.add(MaxPooling2D((2,2)))

model.add(Conv2D(128,(5,5),activation='relu'))
model.add(MaxPooling2D((2,2)))

model.add(Conv2D(256,(3,3),activation='relu'))
model.add(MaxPooling2D((2,2)))

model.add(Dropout(0.2))
model.add(Flatten())

model.add(Dense(256,activation="relu"))
model.add(Dense(128,activation="relu"))
model.add(Dense(64,activation="relu"))
```


this is our model 

here we are using softmax activation for multi classification

Accuracy came out to be : 93 



 But here comes my favourite part 
# TRANSFER learning

From keras.applications import the model you want
i am using MobileNetV2,InceptionV3,VGG16

here we will be iteratin over all models one by one to check all of them



Customize each model for our data's input and output , uk , cut off the head ,to take the weights and use them in our model


The function used :

#### Create Model

- first set base model.trainable = False,so the base model params are freezed
- then dense layers , and at end , pass the num_classes

#### Train model
 - here the usual thingy ,just with plot


Now iterate over all of them 


And finally our last test with images
btw mobilenet did good