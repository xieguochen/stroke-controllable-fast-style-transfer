﻿# Stroke Controllable Fast Style Transfer

This repository contains the public release of the Python implementation of stroke controllable fast style transfer.

[**Stroke Controllable Fast Style Transfer with Adaptive Receptive Fields**](https://arxiv.org/abs/1802.07101)

If you use this code or find this work useful for your research, please cite:
```
@article{Jing,
archivePrefix = {arXiv},
arxivId = {arXiv:1802.07101v2},
author = {Yongcheng Jing, Yang Liu, Yezhou Yang, Zunlei Feng, Yizhou Yu, Mingli Song},
title = {{Stroke Controllable Fast Style Transfer with Adaptive Receptive Fields}},
year={2018}
}
```

## Getting Started

Implemented and tested on Ubuntu 14.04 with Python 2.7 and Tensorflow 1.4.1.

### Dependencies
* [Tensorflow](https://www.tensorflow.org/)
* [Numpy](www.numpy.org/)
* [Pillow](https://pypi.python.org/pypi/Pillow/)
* [Scipy](https://www.scipy.org/)

### Download pre-trained VGG-19 model
The VGG-19 model of tensorflow is adopted from [VGG Tensorflow](https://github.com/machrisaa/tensorflow-vgg) with few modifications on the class interface. The VGG-19 model weights is stored as .npy file and could be download from [Google Drive](https://drive.google.com/file/d/0BxvKyd83BJjYY01PYi1XQjB5R0E/view?usp=sharing) or [BaiduYun Pan](https://pan.baidu.com/s/1o9weflK). After downloading, copy the weight file to the **/vgg19** directory

## Basic Usage
### Train the network
Use train.py to train a new stroke controllable style transfer network. Run `python train.py -h` to view all the possible parameters. The dataset used for training is MSCOCO train 2014 and could be download from [here](http://cocodataset.org/#download), or we provide a random selected 2k images from MSCOCO. Example usage:

```
$ python train.py \
    --style /path/to/style_image.jpg \
    --train_path /path/to/MSCOCO_dataset \
    --sample_path /path/to/content_image.jpg
```

### Freeze model
Use pack_model.py to freeze the saved checkpoint. Run `python pack_model.py -h` to view all parameter. Example usage:

```
$ python pack_model.py \
    --checkpoint_dir ./examples/checkpoint/some_style \
    --output ./examples/model/some_style.pb
```

### Inference
Use inference_style_transfer.py to inference the content image based on the freezed style model. Set `--interp N` to enable interpolation inference where `N` is the number of the continuous stroke results.

```
$ python inference_style_transfer.py \
    --model ./examples/model/some_style.pb \
    --serial ./examples/serial/default/ \
    --content ./examples/content/some_content.jpg
```

## Contact

Feel free to contact us if there is any question (Yang Liu lyng_95@zju.edu.cn)
