# App AI using Yolov3 Android 
## Tool:
- OpenCV 3.4.3
- Android Studio
- Tensorflow 1.13.1
- DW2TF-1.1 or DW2TF-1.2 (Don't using DW2TF-1.0)
- Yolov3 Tiny
## Main
### 1. Convert Yolov3-tiny model of darknet to darkflow
- clone DW2TF-1.2 (in last release) from here [DW2TF-1.2](https://github.com/jinyu121/DW2TF/releases/tag/v1.2)
Problem with DW2TF-1.0 (Yolov3, Yolov3-tiny,... be affected). What is problem? [Problem](https://github.com/jinyu121/DW2TF/issues/30)
- Download (or train) Yolov3 tiny model and config file in darknet (.cfg and .weight).
- Launch DW2TF conversion as mentioned on the github
```python3
python3 main.py \
--cfg 'data/yolov3-tiny.cfg' \
--weights 'data/yolov3-tiny.weights' \
--output 'data/' \
--prefix 'yolov3-tiny/' \
--gpu 0
```
- Conver Darkflow to tensorflow for android. Launch freeze_graph to have a single bp graph file:
```python3
 freeze_graph  \
 --input_graph yolov3-tiny.pb  \
 --input_checkpoint yolov3-tiny.ckpt  \
 --input_binary=true  \
 --output_graph=ultimate_yolov3.bp  \
 --output_node_names=yolov3-tiny/convolutional10/BiasAdd
```
- Note: 
For older version of Yolo you can use darkflow tool [Order](https://github.com/thtrieu/darkflow),Load:
```python3
./flow --model ../data/yolov2-tiny.cfg --load ../data/yolov2-tiny.weights --savepb
```
You can download [Yolo](https://pjreddie.com/darknet/yolo/) at offical page

