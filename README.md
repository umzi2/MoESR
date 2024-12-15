# MoESR: Mamba out Excitation Super-Resolution
This SISR (Single Image Super-Resolution) architecture is based on the [GatedCNNBlock](https://github.com/yuweihao/MambaOut/blob/main/models/mambaout.py#L119), introduced in the [MambaOut](https://github.com/yuweihao/MambaOut) repository. While technically the architecture has no direct connection to Mamba, I decided to retain the reference in the name to support the original author's joke. Previously, I developed the [MoSR](https://github.com/umzi2/MoSR) architecture based on this approach, and technically, MoESR is an extended version of it. The main goal of this extension is to compete with [ESRGAN](https://github.com/xinntao/ESRGAN), which remains one of the best in the mid-range segment of convolutional networks.
## Testing

### Acknowledgments  
Special thanks to **[the-database](https://github.com/the-database)** for conducting the testing and creating the pre-trained model.

### Training Setup  
- **Training framework:** [trainner-redux](https://github.com/the-database/traiNNer-redux)
- **Hardware:** RTX 4090 GPU  

### Training Settings  
- **Batch size:** 32  
- **LQ size:** 64  
- **EMA:** 0.999  
- **Loss function:** MS-SSIM_L1  
Val set: Urban100
```mermaid
xychart-beta
    title "B: MoESR vs ESRGAN"
    x-axis [5k, 50k, 100k, 150k, 200k, 250k, 300k, 350k, 400k, 450k, 500k]
    y-axis "SSIM (higher is better)"
    line [0.7481029033660889, 0.7973534464836121, 0.8052924275398254, 0.8097050786018372, 0.811339795589447, 0.8130168318748474, 0.8137122392654419, 0.8144168853759766, 0.814674973487854, 0.8149675130844116, 0.8150919079780579]
    line [0.7562176585197449, 0.8062689304351807, 0.8118854761123657, 0.8150879740715027, 0.8162787556648254, 0.8170512914657593, 0.8173067569732666, 0.8174617290496826, 0.8176395893096924, 0.8176536560058594, 0.8176558017730713]

```
|model_name|psnr|ssim|
|-|-|-|
|ESRGAN|26.98|0.8151|
|MoESR|**27.05**|**0.8176**|

pretrain safetensors - [original](https://github.com/the-database/traiNNer-redux/releases/download/pretrained-models/4x_DF2K_MoESR_500k.safetensors)

pretrain pth - [convert](https://drive.google.com/drive/u/1/folders/1DSTvXoAM0qV6cF7QUoKth2Yd8h0oBKsz)

[detect code](https://github.com/rewaifu/resselt/blob/main/resselt/archs/moesr/__init__.py#L9)
