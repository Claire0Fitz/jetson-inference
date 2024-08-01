
# Project Name

My project is for Oregon residents and visitors. My project uses image recognition to tell the user what common Oregon animal is in the photo that they uploaded. This can be useful to learn more about the area and what you are encountering in the wilderness. 

The common animals it works for are:
1. Black Bear
2. Bobcat
3. Coyote
4. Grey Wolf
5. Racoon
6. Bald Eagle
7. Elk
(8. None)

Racoon test image:
![test](https://github.com/user-attachments/assets/8a25f914-a3bd-44a9-a2c9-8154c4ecbb4c)

## The Algorithm

First, I used Resnet-18, a pretrained model that is already downloaded onto the jetson nano, to recognize different common animals in Oregon. It is not made to do this which is why I needed to train it.

Secondly, I used datasets I found on kaggle to train the model. I had 8 categories: Black Bear, Bobcat, Coyote, Grey Wolf, Racoon, Bald Eagle, Elk, and None. 
I organized my data into three folders: test, train, and validation. The training set contained roughly 470 images per category, the validation set had about 100 images, and the test set included around 100 images. Training the model involved running a pre-written Python script from the module to help the network learn to recognize the seven different animals. 

Once trained the model was about to recognize which Oregonian animal was pictured. Thirdly, I exported the now ONNX formatted model, saving it to the jetson nano. 

Resnet 18: ResNet-18 is a PyTorch-based machine learning framework designed to detect and classify items in images into various categories. 

## Running this project

1. Download resnet-18 or check if resnet-18 is downloaded onto your jetson nano.
2. Download the files in the github to your jetson nano.
3. Download the data (photos) onto the jetson.
4. Cd into the jetson-inference folder and run: ./docker/run.sh
5. Cd into jetson-inference/python/training/classification
6. Train model using data by using this code: python3 train.py--model-dir=models/animals data/animals
7. Allow resnet-18 model to train for a minimum of ten epochs. The more the merrier tho! (I trained mine for more.)

## Exporting
1. Check you are in the jetson-inference/python/training/classification folder (if you are not, cd into it).
2. Run: python3 onnx_export.py --model-dir=models/animals
3. After you run it, if it is sucessful, there will be a model called "resnet18.onnx" in the jetson-inference/python/training/classification/models/animals folder.

## Video of how my model works
https://youtu.be/bn5ERX3UDd8
