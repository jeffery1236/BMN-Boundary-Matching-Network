# Ablation Studies on Boundary-Matching Network for Temporal Action Localization

A pytorch-version implementation codes of paper:
 "BMN: Boundary-Matching Network for Temporal Action Proposal Generation",
  which is accepted in ICCV 2019. 

[[Arxiv Preprint]](https://arxiv.org/abs/1907.09702)

## Result


| AN     | BMN Results  | Baseline Reproduction   | Improvements over Baseline   |
| ------ | ------ 		| ------ 		| ------ 		|
| AR@1   | 33.6%  		| 33.6%  		| 33.4%  		|
| AR@5   | 49.9%  		| 49.1%  		| 49.8%  		|
| AR@10  | 57.1%  		| 56.5%  		| 57.3%  		|
| AR@100 | 75.5%  		| 75.2%  		| 75.4%  		|
| AUC    | 67.7%   		| 66.9%   		| 67.5%   		|

## Prerequisites

These code is  implemented in Pytorch 1.9.1 + Python 3.8.10. 


## Download Datasets

The two-stream dataset of ActivityNet can be downloaded
 [here](https://paddlemodels.bj.bcebos.com/video_detection/bmn_feat.tar.gz). Which is taken from [this](https://github.com/PaddlePaddle/PaddleVideo/blob/develop/docs/en/dataset/ActivityNet.md) repository. The two-stream dataset should be extracted into `data/activitynet_feature_cuhk/fix_feat_100` for the code to train.

## Training and Testing  of BMN

All configurations of project are saved in opts.py, where you can modify training, model, and inference parameter.

1. To train the model:
```
python main.py --mode train --experiment_name vanilla_model
```
`experiment_name` is simply the name of this experiment. It should be noted that additional parameters would be necessary to apply necessary data augmentation. These parameters include `reverse`, `max_shift`, `shift_prob`, `s_and_e`.

2. To get the inference proposal of the validation videos and evaluate the proposals with recall and AUC in a normal model, simply run the following code.

```
python main.py --mode inference --forward_model vanilla_model
```

However, to run inference proposal on the ensemble model, run the following code.

```
python main.py --mode inference --forward_model vanilla_model --reverse_model reverse_model --ensemble 1
```

## Group name change
We would like to note that our group name changed from group 9 to group 2 during the semester. Therefore, some documentation may indicate this discrepency.

## Reference

This implementation largely borrows from [BMN](https://github.com/JJBOY/BMN-Boundary-Matching-Network) by [JJBOY](https://github.com/JJBOY)

Base paper:[BMN: Boundary-Matching Network for Temporal Action Proposal Generation](https://arxiv.org/abs/1907.09702)

