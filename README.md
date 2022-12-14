## Requirements ##
- 64-bit Python 3.8 and PyTorch 1.9.0 (or later). 
- CUDA toolkit 11.1 or later.
- GCC 7 or later compilers. The recommended GCC version depends on your CUDA version; see for example, CUDA 11.4 system requirements.
- Use the following commands with Miniconda3 to create and activate your PG Python environment:
  - ```conda env create -f environment.yml```
  - ```conda activate sgxl```
  
## Data Preparation ##
For a quick start, you can download the few-shot datasets provided by the authors of [FastGAN](https://github.com/odegeasslbc/FastGAN-pytorch). You can download them [here](https://drive.google.com/file/d/1aAJCZbXNHyraJ6Mi13dSbe7pTyfPXha0/view). To prepare the dataset at the respective resolution, run
```
python dataset_tool.py --source=./data/pokemon --dest=./data/pokemon256.zip \
  --resolution=256x256 --transform=center-crop
```
#### Training

Training StyleGAN-XL on Pokemon:

```
python train.py --outdir=./training-runs/pokemon --cfg=stylegan3-t --data=./data/pokemon16.zip \
    --gpus=8 --batch=64 --mirror=1 --snap 10 --batch-gpu 8 --kimg 10000 --syn_layers 10
```

For a class-conditional dataset (ImageNet, CIFAR-10), add the flag ```--cond True ```. The dataset needs to contain the class labels.



## Trained Models ##
- Model with lower resolution: https://drive.google.com/file/d/1cKtONTnrNlccgNPq1JGabKzfLbWBUFOY/view?usp=sharing
- Model with higher resolution: https://drive.google.com/file/d/1nG8Rz69LPP7YfEyRLwJTlgLmxf3dhMh0/view?usp=sharing
