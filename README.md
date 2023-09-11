# MV2D
 
[Object as Query: Lifting any 2D Object Detector to 3D Detection](https://arxiv.org/abs/2301.02364). 



## Preparation
This implementation is built upon [PETR](https://github.com/megvii-research/PETR/tree/main), and can be constructed as the [install.md](https://github.com/megvii-research/PETR/blob/main/install.md).

* Environments  
  Linux, Python == 3.8.10, CUDA == 11.3, pytorch == 1.11.0, mmcv == 1.6.1, mmdet == 2.25.1, mmdet3d == 1.0.0, mmsegmentation == 0.28.0   

* Detection Data   
Follow the mmdet3d to process the nuScenes dataset (https://github.com/open-mmlab/mmdetection3d/blob/master/docs/en/data_preparation.md).

* Pretrained weights   
We use nuImages pretrained weights from [mmdetection3d](https://github.com/open-mmlab/mmdetection3d/tree/main/configs/nuimages). Download the pretrained weights and put them into `weights/` directory. 

* After preparation, you will be able to see the following directory structure:  
  ```
  MV2D
  ├── mmdetection3d
  ├── configs
  ├── mmdet3d_plugin
  ├── tools
  ├── data
  │   ├── nuscenes
  │     ├── ...
  ├── weights
  ├── README.md
  ```

## Train & Inference
<!-- ```bash
git clone https://github.com/tusen-ai/MV2D.git
``` -->
```bash
cd MV2D
```
You can train the model following:
```bash
bash tools/dist_train.sh configs/mv2d/exp/mv2d_r50_frcnn_two_frames_1408x512_ep24.py 8 
```
You can evaluate the model following:
```bash
bash tools/dist_test.sh configs/mv2d/exp/mv2d_r50_frcnn_two_frames_1408x512_ep24.py work_dirs/mv2d_r50_frcnn_two_frames_1408x512_ep24/latest.pth 8 --eval bbox
```