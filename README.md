# UnseenNet
## Introduction
## Requirements
$ sudo apt install python3-opencv
$ pip install Cython
$ pip install -r requirements.txt
Download chromedriver: https://chromedriver.chromium.org/ and Save in UnseenNet/Googlechrome_Installation/

## Install
## Train
```train
$ python3 main.py --top 10 --unseen_classname 'tunnel' --limit 2500 --chromedriver UnseenNet/Googlechrome_Installation/chromedriver --model_type yolo3_mobilenetv3small --weights_path YOLOv3_MobileNetv3/weights/Strong_Baseline_Detector_Weights.h5 --annotation_file Training_Data/annotations --classes_path YOLOv3_MobileNetv3/configs --anchors_path=YOLOv3_MobileNetv3/configs/yolo3_anchors.txt --image
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
