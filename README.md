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

Tips: Don't forget to pull the latest version of "classroom" repo.

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
python track.py --device 0 --source <YOUR DETECT MP4 FILE> --yolo-weights weights/<YOUR BEST PTH WEIGHT FILE> --reid-weights weights/osnet_x1_0_imagenet.pt --img 1280 --save-vid --agnostic-nms
```
**Tips:** Our best weight is "yolov5l_best.pt"

</details>

<details>
<summary>Training</summary>

```bash
cd yolov5
python train.py --img 960 --batch 4 --workers 4 --device 0 --epochs 300 --cfg <PRETRAIN NETWORK CFG YAML FILE> --data <DATA CFG YAML FILE> --weights <pretrain-weight-file>
```
Here is an example:

```bash
python train.py --img 960 --batch 4 --workers 4 --device 2 --epochs 300 --cfg yolov5l.yaml --data school.yaml --weights yolov5l.pt
```

</details>

<details>
<summary>Pretrained Checkpoints</summary>

| Model                                                                                                | size<br><sup>(pixels) | mAP<sup>val<br>50-95 | mAP<sup>val<br>50 | Speed<br><sup>CPU b1<br>(ms) | Speed<br><sup>V100 b1<br>(ms) | Speed<br><sup>V100 b32<br>(ms) | params<br><sup>(M) | FLOPs<br><sup>@640 (B) |
|------------------------------------------------------------------------------------------------------|-----------------------|----------------------|-------------------|------------------------------|-------------------------------|--------------------------------|--------------------|------------------------|
| [YOLOv5n](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5n.pt)                   | 640                   | 28.0                 | 45.7              | **45**                       | **6.3**                       | **0.6**                        | **1.9**            | **4.5**                |
| [YOLOv5s](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5s.pt)                   | 640                   | 37.4                 | 56.8              | 98                           | 6.4                           | 0.9                            | 7.2                | 16.5                   |
| [YOLOv5m](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5m.pt)                   | 640                   | 45.4                 | 64.1              | 224                          | 8.2                           | 1.7                            | 21.2               | 49.0                   |
| [YOLOv5l](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5l.pt)                   | 640                   | 49.0                 | 67.3              | 430                          | 10.1                          | 2.7                            | 46.5               | 109.1                  |
| [YOLOv5x](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5x.pt)                   | 640                   | 50.7                 | 68.9              | 766                          | 12.1                          | 4.8                            | 86.7               | 205.7                  |
|                                                                                                      |                       |                      |                   |                              |                               |                                |                    |                        |
| [YOLOv5n6](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5n6.pt)                 | 1280                  | 36.0                 | 54.4              | 153                          | 8.1                           | 2.1                            | 3.2                | 4.6                    |
| [YOLOv5s6](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5s6.pt)                 | 1280                  | 44.8                 | 63.7              | 385                          | 8.2                           | 3.6                            | 12.6               | 16.8                   |
| [YOLOv5m6](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5m6.pt)                 | 1280                  | 51.3                 | 69.3              | 887                          | 11.1                          | 6.8                            | 35.7               | 50.0                   |
| [YOLOv5l6](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5l6.pt)                 | 1280                  | 53.7                 | 71.3              | 1784                         | 15.8                          | 10.5                           | 76.8               | 111.4                  |
| [YOLOv5x6](https://github.com/ultralytics/yolov5/releases/download/v6.2/yolov5x6.pt)<br>+ [TTA][tta] | 1280<br>1536          | 55.0<br>**55.8**     | 72.7<br>**72.7**  | 3136<br>-                    | 26.2<br>-                     | 19.4<br>-                      | 140.7<br>-         | 209.8<br>-             |

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
