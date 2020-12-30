# Schistosoma Mansoni Eggs Detector

## Test platform

* **Google Colaboratory**, ```tensorflow-cpu 1.14.0```,```keras 2.1.5```, ```python 3.7```


## Introduction
This repo is based on [qqwweee/keras-yolo3](https://github.com/qqwweee/keras-yolo3).

## Prepare own dataset

Training on own dataset is quite simple, first download pre trained weights from darknet


into ```model_data/```

And provide ```model_data/classes.txt``` which contains the class name of detecting objects, here I provide a example for only one class detection task.

And then all you need is to prepare ```train.txt``` in the same directory with ```train.py```, each line of train.txt is of this format: ```/pat/to/img1 xmin,y_min,x_max,y_max,id```, remember no ```<space>``` before/after ```,``` and an ```<space>``` between ```/path/to/img1``` and ```xmin```. Here I provide a example ```own_train.txt```, remember id starts from 0.

like ```imgs/1.jpg 147,30,437,215,0 147,30,437,215,1``` for two objects labelled in one image, ```<space>``` shall be inserted between two labels.

## Training

```python train.py``` will start training, I recommend reading ```train.py``` carefully before starting. If memory out, change batchsize in ```train.py```

The model trained will be stored in ```logs/000/``` , please check.

## Inference

After training, ```yolo_detect.py``` will detect objects on image while you type the image path.

Usage:

```python yolo_detect.py --model_path /path/to/models```, remember to use the path to models trained stored in ```logs/000/``` mentioned above.
