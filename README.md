<h1 align="center">Lip Reader: End-to-End Visual Speech Recognition Model</h1>

<div align="center">

[📘Introduction](#Introduction) |
[🛠️Preparation](#Preparation) |
[📊Benchmark](#Benchmark-evaluation) |
[🔮Inference](#Speech-prediction) |
[🐯Overview](#Overview) |

</div>

## Authors

Prithvi Yadav , Mukul Godara , Rajat Som

 
## Introduction

This is the repository of End-to-End Visual Speech Recognition Model which is the successor of [End-to-End Audio-Visual Speech Recognition with Conformers](https://arxiv.org/abs/2102.06657). By using this repository, you can achieve the performance of 19.1%, 1.0% and 0.9% WER for automatic, visual, and audio-visual speech recognition (ASR, VSR, and AV-ASR) on LRS3.


## Preparation

1. Clone the repository and enter it locally:

```Shell
git clone https://github.com/mpc001/Visual_Speech_Recognition_for_Multiple_Languages
cd Visual_Speech_Recognition_for_Multiple_Languages
```

2. Setup the environment.

```Shell
conda create -y -n autoavsr python=3.8
conda activate autoavsr
```

3. Install pytorch, torchvision, and torchaudio by following instructions [here](https://pytorch.org/get-started/), and install all packages:

```Shell
pip install -r requirements.txt
conda install -c conda-forge ffmpeg
```

4. Download and extract a pre-trained model and/or language model from [model zoo](#Model-Zoo) to:

- `./benchmarks/${dataset}/models`

- `./benchmarks/${dataset}/language_models`

5. [For VSR and AV-ASR] Install [RetinaFace](./tools) or [MediaPipe](https://pypi.org/project/mediapipe/) tracker.

### Benchmark evaluation

```Shell
python eval.py config_filename=[config_filename] \
               labels_filename=[labels_filename] \
               data_dir=[data_dir] \
               landmarks_dir=[landmarks_dir]
```

- `[config_filename]` is the model configuration path, located in `./configs`.

- `[labels_filename]` is the labels path, located in `${lipreading_root}/benchmarks/${dataset}/labels`.

- `[data_dir]` and `[landmarks_dir]` are the directories for original dataset and corresponding landmarks.

- `gpu_idx=-1` can be added to switch from `cuda:0` to `cpu`.

### Speech prediction

```Shell
python infer.py config_filename=[config_filename] data_filename=[data_filename]
```

- `data_filename` is the path to the audio/video file.

- `detector=mediapipe` can be added to switch from RetinaFace to MediaPipe tracker.

### Mouth ROIs cropping

```Shell
python crop_mouth.py data_filename=[data_filename] dst_filename=[dst_filename]
```

- `dst_filename` is the path where the cropped mouth will be saved.


## Overview

We support a number of datasets for speech recognition:

- [x] [Lip Reading Sentences 2 (LRS2)](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrs2.html)
- [x] [Lip Reading Sentences 3 (LRS3)](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrs3.html)
- [x] [Chinese Mandarin Lip Reading (CMLR)](https://www.vipazoo.cn/CMLR.html)
- [x] [CMU Multimodal Opinion Sentiment, Emotions and Attributes (CMU-MOSEAS)](http://immortal.multicomp.cs.cmu.edu/cache/multilingual)
- [x] [GRID](http://spandh.dcs.shef.ac.uk/gridcorpus)
- [x] [Lombard GRID](http://spandh.dcs.shef.ac.uk/avlombard)
- [x] [TCD-TIMIT](https://sigmedia.tcd.ie)





