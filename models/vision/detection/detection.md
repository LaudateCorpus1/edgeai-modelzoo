# Object Detection Benchmark

## Introduction
Object Detection from Image (a.k.a. 2D Object Detection) is an important problem in Computer Vision. This page describes some of the popular Object Detection models.


## Datasets

**COCO** dataset: COCO is a large scale object detection, segmentation and captioning dataset. In this page we make use of the detection part of COCO dataset. COCO 2017 dataset is being used, unless otherwise mentioned. Accuracy evaluation is done on the validation split of COCO 2017, unless otherwise mentioned.


## Models 
The models are grouped in terms of repositories used to train them or the repositories through they are made available.


### Jacinto-AI/Pytorch-MMDetection
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/edgeai-mmdet/)
- [**Training Source Code**](https://git.ti.com/cgit/jacinto-ai/pytorch-mmdetection/about/)

This is our fork of the popular mmdetection training framework for object detection. We provide several optimized, embedded friendly configurations that provide high throughput on our SoCs. One can train and export models to onnx format, and can then be used in our fork of onnxruntime. Please visit the link above for more information.

|Dataset |Model Name                       |Input Size |GigaMACS  |AP[0.5:0.95]%, AP50%|Available|Notes |
|--------|---------------------------------|-----------|----------|--------------------|---------|----- |
|        |**SSD models**               
|COCO    |MobileNetV2+SSDLite              |512x512    |**1.67**  |**25.1**, 43.1      |         |      |
|COCO    |MobileNetV2+FPN+SSDLite          |512x512    |**2.29**  |**27.2**, 45.7      |         |      |
|COCO    |MobileNetV2+FPN+SSDLite          |768x768    |**5.83**  |**29.0**, 47.8      |         |      |
|-
|COCO    |RegNetX400MF+SSDLite             |320x320    |**1.12**  |**24.1**, 41.0      |         |      |
|COCO    |RegNetX800MF+FPN+SSDLite         |512x512    |**6.03**  |**32.8**, 52.8      |         |      |
|COCO    |RegNetX1.6GF+FPN+SSDLite         |768x768    |**24.19** |**37.0**, 57.3      |         |      |
|COCO    |RegNetX1.6GF+BiFPN168x4+SSDLite  |768x768    |**25.37** |**39.8**, 58.4      |         |      |
|        |**YOLOV3 models**
|COCO    |YOLOv3(LeakyReLU)                |416x416    |**33.0**  |**31.0**, 52.1      |         |Fine tuned to use fixed size |
|COCO    |YOLOv3(ReLU)                     |416x416    |**33.0**  |**30.7**, 51.2      |         |Fine tuned to use fixed size and ReLU |
|COCO    |RegNetX+YOLOV3Lite               |416x416    |**3.6**   |**26.9**, 46.9      |         |      |
|COCO    |RegNetX+YOLOV3Lite               |512x512    |**10.48** |**30.8**, 51.9      |         |      |
|-
|COCO    |ResNet50+FPN+SSD                 |512x512    |**30.77** |**31.2**, 52.2      |         |      |
|        |**RetinaNet models**
|COCO    |RegNetX800MF+FPN+RetinaNetLite   |512x512    |**11.08** |**33.0**, 50.8      |         |      |


### Open-MMLab/MMDetection
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/mmdet/)
- [Training Source Code](https://github.com/open-mmlab/mmdetection)

|Dataset |Model Name                    |Input Size |GigaMACS  |AP[0.5:0.95]%, AP50%|Available|Notes |
|--------|------------------------------|-----------|----------|--------------------|---------|----- |
|        |**YOLOV3 models**
|COCO    |YOLOv3(LeakyReLU)             |(416,416)  |**33.0**  |**30.9**            |         |      |
|COCO    |YOLOv3(LeakyReLU)             |(608,608)  |**70.59** |**33.4**            |         |      |
|        |**SSD model**
|COCO    |VGG16+SSD                     |512x512    |**98.81** |**29.34**           |         |      |
|        |**RetinaNet models**
|COCO    |ResNet50+FPN+RetinaNet        |(1536,768) |**275.5** |**37.0**            |         |      |
|COCO    |ResNet50+FPN+RetinaNet        |512x512    |**68.88** |**29.0**            |         |      |


### Tensorflow TPU Models
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/tf-tpu/)
- [Training Source Code](https://github.com/tensorflow/tpu/tree/master/models/official)

|Dataset |Model Name                    |Input Size |GigaMACS  |AP[0.5:0.95]%, AP50%|Available|Notes |
|--------|------------------------------|-----------|----------|--------------------|---------|----- |
|COCO    |ssdlite_mobiledet_edgetpu_320x320_coco_2020_05_19|320x320|1.534|**25.9**  |Y        |      |
|COCO    |ssdlite_mobiledet_dsp_320x320_coco_2020_05_19|320x320|2.818|**28.9**      |Y        |      |


### TensorFlow Model Garden - Object Detection API Models Using Tensorflow 1.0 
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/tf1-models/)
- [Training Source Code](https://github.com/tensorflow/models/tree/master/research/object_detection)
- [Training Documentation](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf1.md)
- [Object Detection API Model Zoo For Tensorflow 1.0](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf1_detection_zoo.md)

|Dataset |Model Name                    |Input Size |GigaMACS  |AP[0.5:0.95]%, AP50%|Available|Notes   |
|--------|------------------------------|-----------|----------|--------------------|---------|--------|
|COCO    |ssd_mobilenet_v1_coco_2018_01_28|300x300  |1.237      |**23.0**           |Y         |Also used in MLPerf benchmark |
|COCO    |ssd_mobilenet_v2_300          |300x300    |1.875     |**22.0**            |Y         |Also used in MLPerf benchmark |
|COCO    |ssdlite_mobilenet_v2_coco_2018_05_09|300x300|0.75    |**22.0**            |Y         |        |


### TensorFlow Model Garden - Object Detection API Models Using Tensorflow 2.0
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/tf2-models/)
- [Training Source Code](https://github.com/tensorflow/models/tree/master/research/object_detection)
- [Training Documentation](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2.md)
- [Object Detection API Model Zoo For Tensorflow 2.0](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md)


### Models trained using github.com/google/automl
- [**Information about our training**](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/about/models/vision/detection/coco/google-automl/README.md)
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/google-automl/)
- [More Information - github.com/google/automl](https://github.com/google/automl)


|Dataset |Model Name                              |Input Size |GigaMACS  |AP[0.5:0.95]%, AP50%|Available|Notes |
|--------|----------------------------------------|-----------|----------|--------------------|---------|----- |
|        |**Our training - Lite models**
|COCO    |efficientdet-lite0_bifpn_maxpool2x2_relu_ti-lite|512x512    |**2.50**  |33.61, 52.27        |Y        |ti-lite flavour|
|          |**Model from original repository**
|COCO    |EfficientDet-D0                       |512x512    |          |34.3, 53.0          |         |      |

Note: EfficientDet-Lite (or efficientdet-lite) is the embedded friendly variant of EfficientDet. We have also done some additional modifications on top of the original EfficientDet-Lite to better suite our platform (which we referred to as ti-lite flavour in the table). Please refer to [**information about our training**](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/about/models/vision/detection/coco/google-automl/README.md) for more details.


## Models From github.com/onnx/models
- [Models Link](https://git.ti.com/cgit/jacinto-ai/jacinto-ai-modelzoo/tree/models/vision/detection/coco/onnx-models/)
- [More Information - github.com/onnx/models](https://github.com/onnx/models)


## Notes
- GigaMACS: Complexity in Giga Multiply-Accumulations (lower is better). This is an important metric to watch out for when selecting models for embedded inference.<br>
- Accuracy for Object Detection on COCO dataset primarily uses two accuracy metrics AP[0.5:0.95] and AP50 (in percentages). AP[0.5:0.95] is the Mean of Average Precision values computed at IOUs ranging from 0.5 to 0.95 and averaged. AP50 is the Average Precision computed at 0.5 IoU. If only one accuracy metric is mentioned in a table cell, then it is AP[0.5:0.95]. Be sure to compare using the same metric when comparing across various detectors or configurations.
- The suffix 'Lite' in the name of models such as SSDLite, RetinaNetLite indicates the use of Depthwise convolutions or Grouped convolutions. If the feature extractor (encoder) uses Depthwise Convolutions, then usually Depthwise convolutions are used throughout such models - even in the neck and decoder. If the feature extractor (encoder) uses grouped convolutions as in the case of RegNetX, then grouped convolutions (with the same group size as that of the feature extractor) are used even in the neck and decoder.<br>
- Lite models also uses ReLU activation (instead of complicated activations such as Swish, HSwish etc.) and also does not use other modules that are unfriendly to embedded inference - such as Squeeze And Excitation (SE).
- A fixed resolution in the tables is indicated by *width x height* and it means that the inputs are to be resized to that resolution without preserving the aspect ratio of the image (keep_ratio=False in config files). The resolution after resize can be square (example: 512x512) or non-square (example: 768x384).  Detectors such as SSD [1] and EfficientDet (arXiv:1911.09070) [3] uses this kind of fixed resizing. **It is preferable to use this kind of fixed resolution resize for embedded inference** - at least from an accuracy evaluation point of view (where the actual dataset with variable size images may need to be evaluated upon).<br>
- A resolution range in the tables is indicated with comma (1536,768) - it means that images are resized to fit within this maximum and minimum size - and the aspect ratio of the original image is preserved (keep_ratio=True in config files). Due to this, each resized image may have a different size depending on the aspect ratio of the original image.<br>
- *Mmdetection typically uses a resolution range to train models for most models except SSD. An interesting observation that we had is that such  models trained for non-square resolutions can also be inferred or evaluated using square aspect ratios (with a bit of accuracy drop, of course). This leads to the possibility of reusing the models provided in the [mmdetection model zoo](https://github.com/open-mmlab/mmdetection/blob/master/docs/model_zoo.md) for fixed resolution inference as well.*<br>
- YOLOv3 gives 30.9% AP[0.5:0.95] when evaluated with mmdetection at (416,416). But mmdetection uses variable size resize preserving the aspect ratio which means different images have different input sizes to the models within (416,416) - this kind of inference is not suitable for embedded inference. When inferred at fixed 416x416 resolution, it gives 29.6% AP[0.5:0.95] with mmdetection.<br>


## References

[1] MMDetection: Open MMLab Detection Toolbox and Benchmark, Kai Chen, Jiaqi Wang, Jiangmiao Pang, Yuhang Cao, Yu Xiong, Xiaoxiao Li, Shuyang Sun, Wansen Feng, Ziwei Liu, Jiarui Xu, Zheng Zhang, Dazhi Cheng, Chenchen Zhu, Tianheng Cheng, Qijie Zhao, Buyu Li, Xin Lu, Rui Zhu, Yue Wu, Jifeng Dai, Jingdong Wang, Jianping Shi, Wanli Ouyang, Chen Change Loy, Dahua Lin, https://arxiv.org/abs/1906.07155

[2] The PASCAL Visual Object Classes (VOC) Challenge, Everingham, M., Van Gool, L., Williams, C. K. I., Winn, J. and Zisserman, A.
International Journal of Computer Vision, 88(2), 303-338, 2010, http://host.robots.ox.ac.uk/pascal/VOC/

[2] Microsoft COCO: Common Objects in Context, Tsung-Yi Lin, Michael Maire, Serge Belongie, Lubomir Bourdev, Ross Girshick, James Hays, Pietro Perona, Deva Ramanan, C. Lawrence Zitnick, Piotr Dollár, https://arxiv.org/abs/1405.0312, https://cocodataset.org/

[3] SSD: Single Shot MultiBox Detector, Wei Liu, Dragomir Anguelov, Dumitru Erhan, Christian Szegedy, Scott Reed, Cheng-Yang Fu, Alexander C. Berg, https://arxiv.org/abs/1512.02325

[4] Focal Loss for Dense Object Detection, Tsung-Yi Lin, Priya Goyal, Ross Girshick, Kaiming He, Piotr Dollár, https://arxiv.org/abs/1708.02002

[5] Feature Pyramid Networks for Object Detection Tsung-Yi Lin, Piotr Dollár, Ross Girshick, Kaiming He, Bharath Hariharan, Serge Belongie, https://arxiv.org/abs/1612.03144

[6] YOLOv3: An Incremental Improvement, Joseph Redmon, Ali Farhadi, https://arxiv.org/abs/1804.02767

[7] Objects as Points, Xingyi Zhou, Dequan Wang, Philipp Krähenbühl, https://arxiv.org/abs/1904.07850

[8] EfficientDet: Scalable and Efficient Object Detection, Mingxing Tan, Ruoming Pang, Quoc V. Le, https://arxiv.org/abs/1911.09070






