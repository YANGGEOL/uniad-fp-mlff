# UniAD+

An enhancement method for UniAD models.

Original official paper: [A Unified Model for Multi-class Anomaly Detection](https://arxiv.org/abs/2206.03687) 

Original official code: [GitHub](https://github.com/zhiyuanyou/UniAD)

## Quick Start

#### Environment

```bash
conda create -n uniad python==3.8

pip install torch==1.13.1+cu117 torchvision==0.14.1+cu117 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu117

pip install -r requirements.txt
```

#### Dataset

##### MVTec-AD:

- Create the MVTec-AD dataset directory. Download the MVTec-AD dataset from [here](https://www.mvtec.com/company/research/datasets/mvtec-ad)  and unzip the file and move some to `./data/MVTec-AD/`. The MVTec-AD dataset directory should be as follows. 

  ```
  |-- data
      |-- MVTec-AD
          |-- mvtec_anomaly_detection
          |-- json_vis_decoder
          |-- train.json
          |-- test.json
  ```

##### ViSA

- Create the ViSA dataset directory and download the ViSA dataset from [here](https://amazon-visual-anomaly.s3.us-west-2.amazonaws.com/VisA_20220922.tar).

- Modify the directory structure to the same as the  MVTec-AD dataset.

  ```
  |-- data
      |-- ViSA
          |-- visa
          	|-- candler
          		|-- ground_truth
          		|-- test
          		|-- train
          	|-- ......
          	|-- pipe_fryum
          |-- json_vis_decoder
          |-- train.json
          |-- test.json
  ```

- Edit train.json and test.json files similar to the MVTec-AD dataset for model training

#### Train or eval

##### MVTec-AD:

- Cd the experiment directory by running `cd ./experiments/MVTec-AD/`. 
- Train for `sh train_torch.sh #NUM_GPUS #GPU_IDS`  and eval for `sh eval_torch.sh #NUM_GPUS #GPU_IDS`
- If trian in 4 GPUs: sh train_torch.sh 4 1,3,4,6

##### ViSA:

- Cd the experiment directory by running `cd ./experiments/ViSA/`. 
- Train for `sh train_torch.sh #NUM_GPUS #GPU_IDS`  and eval for `sh eval_torch.sh #NUM_GPUS #GPU_IDS`
- If train in 4 GPUs: sh train_torch.sh 4 1,3,4,6

**Note**: During eval, please *set config.saver.load_path* to load the checkpoints. 

#### Result

| Class \| Model | UniAD (Dec) | UniAD (Loc) | Ours (Dec) | Ours (Loc) |
| -------------- | ----------- | ----------- | ---------- | ---------- |
| Bottle         | 99.8        | **98**      | **100**    | 97.8       |
| Cable          | **96.1**    | **97.3**    | 94         | 96.5       |
| Capsule        | 87.1        | 98.5        | **91.1**   | **98.6**   |
| Hazmat         | 99.8        | **98**      | **100**    | 97.9       |
| Metal_Nut      | 99.3        | 93.4        | **99.4**   | **95.5**   |
| Pill           | 93.7        | 95.1        | **95**     | **95.8**   |
| Screw          | 88.5        | 98.4        | **91.8**   | **99**     |
| Toothbrush     | 94.1        | 98.4        | 92.2       | 98.2       |
| Transistor     | 99.8        | 98.2        | 99.2       | **98.3**   |
| Zipper         | 95.2        | 96.6        | **98.1**   | **97.5**   |
| Carpet         | 99.7        | 98.5        | 99.6       | 98.2       |
| Grid           | 97.6        | 96.6        | **98.5**   | **97.1**   |
| Leather        | 100         | 98.8        | **100**    | 98.4       |
| Tile           | 99.2        | 92.1        | **99.6**   | 91.8       |
| Wood           | 98.3        | 93.2        | **98.7**   | 92.7       |
| Avg            | 96.5        | 96.7        | **97.1**   | **96.9**   |





