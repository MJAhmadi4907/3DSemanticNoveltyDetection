# 3D Semantic Novelty Detection
## Code from Towards Open Set 3D Learning: Benchmarking and Understanding Semantic Novelty Detection on Pointclouds

> **Abstract:** *Different studies on 3D point cloud have been performed. Multiple Convolutionnal Neural Network (CNN) resulted of these papers setting the base of what is possible to do in the field. The most famous one being Dynamic Graph CNN (DGCNN) and PointNet with it’s evolution PointNet++. The goal of this paper is to describe their performances for each of them and detecting Out Of Distribution (OOD) objects. Furthermore, this study aims to understand the different errors produced by the models performing a failure cases analysis. Later, for the aim of pre-trained model, we will use OpenShape which is trained on a wide range of databases.*

## Introduction

This code allows to replicate all the experiments and reproduce all the results that we included in
our paper.


### Data
Use the prepared script to download all datasets. 

```bash
chmod +x download_data.sh
./download_data.sh
```

A common root for all datasets will be created in project dir, by default named *3D_OS_release_data* .
```
3D_OS_release_data (root)
├─ ScanObjectNN
├─ modelnet40_normal_resampled
```

The absolute path to the datasets root must be passed as **--data_root** argument in all scripts.


### Training

Each experiment requires to choose a backbone (through the config file), a loss function and a source set. For example: 

```bash
# multiple gpus
python classifiers/trainer_cla.py --config cfgs/dgcnn-cla.yaml --exp_name DGCNN_CE_SR1 --src SR1 --loss CE 
```

### Eval 

```bash
# multiple gpus
python  classifiers/trainer_cla.py --config cfgs/dgcnn-cla.yaml --exp_name DGCNN_CE_SR1 --src SR1 --loss CE -mode eval --ckpt_path outputs/DGCNN_CE_SN1/models/model_last.pth

```

Example output:
```bash
Computing OOD metrics with MLS normality score...
AUROC - Src label: 1, Tar label: 0
Src Test - Clf Acc: 0.8522321428571429, Clf Bal Acc: 0.7607892805466309
Auroc 1: 0.7345, FPR 1: 0.7905
Auroc 2: 0.7574, FPR 2: 0.7458
Auroc 3: 0.7440, FPR 3: 0.7719
to spreadsheet: 0.734540224202969,0.7904599659284497,0.7573800391095067,0.7457882069795427,0.7440065016031351,0.7719451371571072
```








## This repo is still under construction
- [x] Upload Code
- [x] Upload Data
- [ ] Acknowledgements
- [x] Link to the arXiv and citation
