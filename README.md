# Yolov5 + StrongSORT with OSNet

<div align="center">
<p>
<img src="trackers/strong_sort/results/output_th025.gif" width="400"/> 
</p>
<br>
<div>
<a href="https://github.com/mikel-brostrom/Yolov5_DeepSort_Pytorch/actions"><img src="https://github.com/mikel-brostrom/Yolov5_DeepSort_Pytorch/workflows/CI%20CPU%20testing/badge.svg" alt="CI CPU testing"></a>
<br>  
<a href="https://colab.research.google.com/drive/18nIqkBr68TkK8dHdarxTco6svHUJGggY?usp=sharing"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
  
</div>

</div>


## Introduction

This repository contains a highly configurable two-stage-tracker that adjusts to different deployment scenarios. The detections generated by [YOLOv5](https://github.com/ultralytics/yolov5), a family of object detection architectures and models pretrained on the [COCO](https://arxiv.org/abs/1405.0312) dataset, are passed to the tracker of your choice. Supported ones at the moment are: [StrongSORT](https://github.com/dyhBUPT/StrongSORT)[](https://arxiv.org/abs/2202.13514) [OSNet](https://github.com/KaiyangZhou/deep-person-reid)[](https://arxiv.org/abs/1905.00953), [OCSORT](https://github.com/noahcao/OC_SORT)[](https://arxiv.org/abs/2203.14360) and [ByteTrack](https://github.com/ifzhang/ByteTrack)[](https://arxiv.org/abs/2110.06864). They can track any object that your Yolov5 model was trained to detect.


<details>
<summary>Installation</summary>

```bash
git clone --recurse-submodules https://github.com/Jackson-coder/classroom_pro.git  # clone recursively
cd classroom_pro
pip install -r requirements.txt  # install dependencies
```
### Get simsun.zip via the following link and unzip it in the root directory.

link：https://pan.baidu.com/s/14WMopYlf4pdOTpNcgLfKPg?pwd=0000 

password：0000 

### Get weights directory via the following link and put it in the root directory.

link：https://pan.baidu.com/s/1dOUVbwSg2rg_pWzd5Emrfg?pwd=0000 
password：0000 

</details>

<details>
<summary>Tracking</summary>

```bash
python track.py --device 3 --source yolov5/test_videos/test2.mp4 --yolo-weights weights/yolov5l.pt --reid-weights weights/osnet_x1_0_imagenet.pt --img 1280 --save-vid --agnostic-nms
```
</details>

<details>
<summary>Training</summary>

```bash
cd yolov5
python train.py --img 960 --batch 4 --workers 4 --device 2 --epochs 300 --cfg yolov5l.yaml --data school.yaml --weights yolov5l.pt
```
</details>


## Cite

If you find this project useful in your research, please consider cite:

```latex
@misc{yolov5-strongsort-osnet-2022,
    title={Real-time multi-camera multi-object tracker using YOLOv5 and StrongSORT with OSNet},
    author={Mikel Broström},
    howpublished = {\url{https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet}},
    year={2022}
}
```
