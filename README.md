# sign-detection-using-yolo-v5" 

## Open labelimg in terminal and annotate the images, move the images in train and test directory where in Images and labels folder data should be stored

## Craete a data.yaml file where location of train and test folder along with classed should be stored.

## Clone yolov5 git "!git clone https://github.com/ultralytics/yolov5.git"

## Move to yolov5 (cloned repo)

## Install requirenments (pip install -r requirenments.txt)

## Download the annotated images data here, we can use curl command, unzip the data

## In yolov5 directory, models folder is presnt which contain all the models we can use. Now we need to modify those configuration based on our requirenment like here in this case we have 6 classes, so modify them accordingly and save it in models folder itself(custom_yolov5s.yaml)

## Now we have to train the model. They have already written everyyhting for training in train.py file
python train.py --img 480 --batch 16 --epochs 300 --data '../data.yaml' --cfg ./models/custom_yolov5s.yaml --weights 'yolov5s.pt' --name yolov5s_results  --cache

## First this will download the model if it is not available then it will start the training

## Now runs folder will be created in yolov5 folder. Yolov5 >> runs >> train >> yolov5s_results >> weights, metrics loss, MAP, Precision everyhting will be mentioned.

## Inside Yolov5 >> runs >> train >> yolov5s_results >> weights, it contain best.pt and last.pt.

## To check the metrics we can use tensorboard

## Now for prediction we have detect.py file alredy given by YOLO
!python detect.py --weights runs/train/yolov5s_results/weights/best.pt --img 480 --conf 0.5 --source ../test/images

## After prediction it will save in runs >> detect >> exp folder

## Now to perform this task in local download the trained model "best.pt" and put it in yolov5 folder

## Create a virtual environment
conda create -n sign_detection python=3.10

### actaivate the virtual env
conda activate sign_detection

## Install the requrienments
pip install -r .\requirements.txt

## RUN Flask app
python app.py