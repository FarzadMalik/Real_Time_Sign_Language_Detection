
# Real Time Sign Language Detection with Tensorflow

With this project one will be able to detect 5 sign language, such as: Yes, No, Good, Thank you, I love you realtime using the webcam.
I made this object detector using python, tensorflow and opencv. Later on, this can be used as a template for any kind of object detection.
![image](https://user-images.githubusercontent.com/107833662/211126009-54a58c9d-8332-42f3-a96d-50adde808203.png)


 I did that in 3 steps:
  #### Prepare labeled images using lblimg

  #### Transfer learning using SSD Mobilenet

  #### Realtime detection using OpenCV and webcam

## Detailed steps:
### 0) Install dependencies
* Make the folder tree for object detection.
* Install lblimg from github.Put it inside tensorflow folder. They have the tutorial on the readme.md. For that we need to install pyqt=5 and lxml first.


### 1) Collect plenty of images for each category using OpenCV
* Made a jupyter notebook named capture_images for auto capturing images
* used opencv to auto capture images and uuid for naming them
* get the camera id, and using that ID create a video capture device
* also capture the frame size when getting the images



### 2) Label the images using lblimg
* run the lblimg from cmd
* configure open directory and save directory. 
* then label the images one by one

### 3) Create a jupyter notebook for training
* I collected the data, trained and tested the data and finally do it Realtime
* First make a skelleton of the notebook in order to make it easier to write the collected

### 4) Setup paths
* Setup default paths for WORKSPACE, SCRIPTS ,API MODEL, ANNOTATIONS, IMAGE,MODEL, PRETRAINED MODEL, CONFIG , CHECKPOINT 
* Be careful about the usage of / and \

### 5) Create label map
* create a dictionary for the labels
* Then from that dictionary create the map in protobuf format

### 6) Create TF Records
* Run the python command
* 2 record file will be created for train and test

### 7) Download pre-trained models from Tensorflow models zoo
* To use the object detection model, object detection package needs to be installed already
* The tutorial is on the tensorflow website
* can download the model garden using command
* But I just did it manually from  I just did it manually from https://github.com/tensorflow/models
* Download pre-trained model from https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md
* Need to look at coco map to select the right one

### 8) Copy model.config to the training folder
* Can copy usimg the copy command
* Also can be done using manually
* I copied it manually

### 9) Update config for transfer learning
* Import Tensorflow, object detection utensil, protobuf
* Setup configuration path
* Use config utulities to grab the config file
* Update the config file using the pipeline.pb2
* First write a shell config and then write it to the directory
* Update number of classes, batch size, checkpoint, checkpoint type, label map for training and testing record


### 10) Train the model
* Can train the model in the jupyter or the cmd
* I chose the cmd because it's a long process and my notebook seems to crash
* The command passes through tf2.py, pre-trained model, pipeline config respectively. Training steps are 30000. More for better results, less for faster training.
* Wait for the training to be finished

### 11) Load train model from checkpoint
* Import label map utility, visualization utility, and model builder
* Grab the modified pipeline
* Build the model using model config
* Load the latest checkpoint (ckpt-32.index) into the pipeline
* Write the detect function where I pass the image and get the detection

### 12) Detect mask Realtime
* I used my webcam for realtime detection 
* Import cv2 and numpy
* Create catagory index
* Setup capture device and realtime object detection script


# Results
### Yes
![Yes](https://user-images.githubusercontent.com/107833662/211126150-a84b3307-6d12-462c-8a20-2825f7886d7e.png)

### No
![No 2](https://user-images.githubusercontent.com/107833662/211126155-f85417df-5f58-4d4c-b20a-6ad7a6e104dc.png)
![No](https://user-images.githubusercontent.com/107833662/211126164-72914761-2f75-4a79-b64e-2e92a52d15e4.png)

### I love you
![I love you](https://user-images.githubusercontent.com/107833662/211126168-33af2c78-4dd0-463f-ae78-8d697f9e6d0a.png)

### Detections aren't always accurate
![object detection](https://user-images.githubusercontent.com/107833662/211126175-4487a5fb-daeb-4f1e-9abb-ce5627830c2f.png)

* From the screenshots it can be seen that in real time the detection model works quite well.
* There are some minor glitches that happen for example detecting externel objects or incorrect detection.
* Results can be improved by training longer, changing pre-trained model or labelling the images with high accuracy.
