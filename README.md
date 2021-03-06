# LipNet: End-to-End Sentence-level Lipreading

The PyTorch implementation of 'LipNet: End-to-End Sentence-level Lipreading' by Yannis M. Assael, Brendan Shillingford, Shimon Whiteson, and Nando de Freitas (https://arxiv.org/abs/1611.01599). We use PyTorch to build the LipNet model with minor changes. This reproduction achieves 13.3%/4.6% WER in unseen/overlapped testing, which exceeds all evaluation metrics in the original paper and reaches **the state-of-the-art performance**.

## Demo

![LipNet Demo](demo.gif)


## Results

|       Scenario          |  Image Size (W x H) |  CER  |     WER    |
|:-----------------------:|:-------------------:|:-----:|:----------:|
|    Unseen speakers (Origin)    | 100 x 50 |    6.7%   |    13.6%   |
|   Overlapped speakers (Origin) | 100 x 50 |    2.0%   |    5.6%    |
|    Unseen speakers (Ours)      | 128 x 64 |  **6.7%** |  **13.3%** |
|   Overlapped speakers (Ours)   | 128 x 64 |  **1.9%** |  **4.6%**  |

**Notes**:

- Contribution to sharing the results of this model is highly appreciated.

## Data Statistics

Following the original split, we use `s1`, `s2`, `s20`, `s22` in unseen speakers testing and choose 255 random sentences from each speaker in overlapped speakers testing.

|             Scenario            |   Train   |  Validation  |
|:-------------------------------:|:---------:|:------------:|
|    Unseen speakers (Origin)     |   28775   |     3971     |      
|   Overlapped speakers (Origin)  |   24331   |     8415     |
|    Unseen speakers (Ours)       |   28837   |     3986     |
|   Overlapped speakers (Ours)    |   24408   |     8415     |


## Data Preparation

We provide cropped lip images in the following links: 

BaiduYun: 链接:https://pan.baidu.com/s/1I51Xf-DzP1UgrXF-S0L5tg  密码:jf0l

Google Drive: https://drive.google.com/drive/folders/1Wn2EJw2101nF59eNDXEto6qXqfgDDucL

Download all parts and concatenate the files using the following command:

```
cat GRID_LIP_160x80_TXT.zip.* > GRID_LIP_160x80_TXT.zip
unzip GRID_LIP_160x80_TXT.zip
rm GRID_LIP_160x80_TXT.zip
```

For establishing a whole lip reading pipeline by yourself, we provide code of face detection and alignment in `scripts/` folder for reference.

## Training And Testing

```
python main.py
```

Data configurations and hyperparameters are configured in `options.py`. Please pay attention that you may need to modify it to make the program work as expected. (e.g. data path, learning rate, batch size, and so on)


## Dependencies

* PyTorch 1.0+
* opencv-python

## Bibtex
    @article{assael2016lipnet,
	  title={LipNet: End-to-End Sentence-level Lipreading},
	  author={Assael, Yannis M and Shillingford, Brendan and Whiteson, Shimon and de Freitas, Nando},
	  journal={GPU Technology Conference},
	  year={2017},
	  url={https://github.com/Fengdalu/LipNet-PyTorch}
	}


## License

The MIT License
