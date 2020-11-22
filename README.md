# UnseenNet
## Introduction
## Requirements
1. Python 3 on Ubuntu 16.04/18.04, tensorflow-gpu, keras, numpy, selenium etc. To install run:
```install
$ sudo apt install python3-opencv
$ pip install Cython
$ pip install -r requirements.txt
```
2. Download chromedriver: https://chromedriver.chromium.org/ and Save in UnseenNet/Googlechrome_Installation/
3. Choose option of training for `unseen` concepts or directly use detcetion demo if you have weights file available.


## Train
It is very easy to use UnseenNet to train for any unseen/new class. Here is an example (ready to try):

```train
$ python3 main.py --unseen_classname 'tunnel' --limit 2500  --top 10 --chromedriver UnseenNet/Googlechrome_Installation/chromedriver --model_type yolo3_mobilenetv3small --weights_path YOLOv3_MobileNetv3/weights/Strong_Baseline_Detector_Weights.h5 --annotation_file Training_Data/annotations --classes_path YOLOv3_MobileNetv3/configs --anchors_path=YOLOv3_MobileNetv3/configs/yolo3_anchors.txt --image
```
Necessary parameters: As the name suggests `--unseen_classname` is to prove name of unseen class like `tunnel`, `--limit` is the number of images to donaload for training, `--top` is the number of seen classes UnseenNet will use to perform Adaptation (0<top<=100), `--chromedriver` is to give the location of driver to download images. 

Optional parameters: `yolo3_mobilenetv3small` is the default model type, `--weights_path` is also set default for `Strong Baseline Detector`, `annotation_file` is to communicate the location of annotations where UnseenNet will save the generated annotations,  `classes_path` is list of classes UnseenNet can detect, and `image` is presently to keep the UnseenNet in image-mode (not video) only.

Please note we used the conventional format of annotations, i.e. 
```format
One row for one image in annotation file;
Row format: image_file_path box1 box2 ... boxN;
Box format: x_min,y_min,x_max,y_max,class_id (no space).
```

## Detect
```demo
$ python3 Demo_Detect.py --model_type yolo3_mobilenetv3small --weights_path weights/building.h5 --classes_path configs/Building.txt --anchors_path=configs/yolo3_anchors.txt --image
```
## Cite
Please cite UnseenNet (and following repositories used in UnseenNet) in your publications if it helps your research:

```cite
anonymous, UnseenNet (2020) , GitHub repository

Google Images Download: https://github.com/hardikvasa/google-images-download

david8862, TF Keras YOLOv4/v3/v2 Modelset (2019), GitHub repository

Adam Yang, MobileNet-Yolov3 (2018), GitHub repository

qqwweee, keras-yolo3 (2018), GitHub repository

allanzelener, YAD2K: Yet Another Darknet 2 Keras (2017), GitHub repository

Redmon, Joseph, and Ali Farhadi. "Yolov3: An incremental improvement." arXiv preprint arXiv:1804.02767 (2018).

Redmon, Joseph, and Ali Farhadi. "YOLO9000: better, faster, stronger." Proceedings of the IEEE conference on computer vision and pattern recognition. 2017.
```

## Contact
anonymous, UnseenNet
