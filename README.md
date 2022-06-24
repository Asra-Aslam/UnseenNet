# UnseenNet
## Introduction
UnseenNet: LSDA-based Fast Training Detector for Unseen Concepts with No Bounding Boxes

## Requirements
1. Python 3 on Ubuntu 16.04/18.04, tensorflow-gpu, keras, numpy, selenium etc. To install run:
```install
$ sudo apt install python3-opencv
$ pip install Cython
$ pip install -r requirements.txt
```
2. Download chromedriver: https://chromedriver.chromium.org/ and save file named "chromedriver" in UnseenNet/Googlechrome_Installation/
3. Choose option of training for `unseen` concepts or directly use detection demo if you have weights and classes path files available. However, for any new/unseen class always starts with `Train and Detect` as this will give you required files to use `Demo Detect` option.
4. Download Strong and Weak Baseline Detector Weights from https://drive.google.com/file/d/19WNdmtbT49GQdSuHHy0e7dodIvxlWJ2F/view?usp=sharing and https://drive.google.com/file/d/1_5mPIu2ivPvKp8UPM6-X_iitedZikYyG/view?usp=sharing 
6. Place both weight files in folder UnseenNet/YOLOv3_MobileNetv3/weights

## Train and Detect
It is very easy to use UnseenNet to train for any unseen/new class. Here is an example (ready to try):

```train
$ python3 UnseenNet.py --unseen_classname 'tunnel' --limit 2500  --top 10 --response_time 5 --chromedriver Googlechrome_Installation/chromedriver --model_type yolo3_mobilenetv3small --weights_path YOLOv3_MobileNetv3/weights/Strong_Baseline_Detector_Weights.h5 --annotation_file Training_Data/annotations --classes_path YOLOv3_MobileNetv3/configs --anchors_path=YOLOv3_MobileNetv3/configs/yolo3_anchors.txt --image
```
Necessary parameters: As the name suggests `--unseen_classname` is to provide name of unseen class like `tunnel`, `--limit` is the number of images to download for training, `--top` is the number of seen classes `UnseenNet` will use to perform Adaptation (0<top<=100), `--chromedriver` is to give the location of driver to download images. 

Optional parameters: `--response_time` is the optional and most useful parameter of UnseenNet. It decides the time of training (default value is 5). We suggest only 5 min of training sufficient for UnseenNet; however, we recommend the maximum value until 50 min. 
`yolo3_mobilenetv3small` is the default model type, `--weights_path` is also set default for `Strong Baseline Detector`, `annotation_file` is to communicate the location of annotations where UnseenNet will save the generated annotations,  `classes_path` is list of classes UnseenNet can detect, `anchors_path` is recommended by YOLOv3, and `image` is presently used to keep the UnseenNet in image-mode (not video) only.

Please note we also used the conventional format of annotations, i.e. 
```format
One row for one image in annotation file;
Row format: image_file_path box1 box2 ... boxN;
Box format: x_min,y_min,x_max,y_max,class_id (no space).
```
UnseenNet will follow steps:
```steps
1. First, it will download images for unseen class (say tunnel)
2. Starts training after computing epochs depending on response-time (default 5 min)
3. Provide an option to continue for `detection` or `quit`.
We can always opt for `quit` and detect maybe later using `Demo Detect` as `UnseenNet` will save `weights` and update `classes_path` file according to new `unseen` class.
```

## Demo Detect
It assumes we have trained weights available in `YOLOv3_MobileNetv3/weights/` and classes path available in `YOLOv3_MobileNetv3/configs/`. For example:
```demo
$ python3 YOLOv3_MobileNetv3/Demo_Detect.py --model_type yolo3_mobilenetv3small --weights_path weights/building.h5 --classes_path configs/Building.txt --anchors_path=configs/yolo3_anchors.txt --image   #----here unseen class name is `building`-------
```

## Cite
Please cite our UnseenNet work below (published in CVPR 2022) in your publications if it helps your research:

```cite
Aslam, Asra. "Detecting Objects in Less Response Time for Processing Multimedia Events in Smart Cities." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2022.

Aslam, Asra, and Edward Curry. "UnseenNet: Fast Training Detector for Any Unseen Concept." arXiv preprint arXiv:2203.08759 (2022).
```

## Contact
Asra Aslam, asra.aslam.7@gmail.com, UnseenNet

