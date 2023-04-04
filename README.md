# MRI-Image-Segmentation-Swin-Unet


# Introduction
This repository contains code for training and testing a TransUNet model on Synapse dataset. The CMD.ipynb notebook is used as a terminal to run the code. The folder structure should be kept the same, otherwise the directories called by the command will need to be changed.

# Code Explanation
CMD.ipynb: this notebook is used as a terminal to run the code.
TransUNet: this folder contains the implementation of the TransUNet model.
data: this folder contains the Synapse dataset.
output: this folder will contain the saved model and test results.
## Training
To train the model, run the following command in the CMD.ipynb notebook:

```
!python3 TransUNet/train.py --dataset Synapse --cfg TransUNet/configs/swin_tiny_patch4_window7_224_lite.yaml --root_path data/Synapse --max_epochs 150  --output_dir output  --img_size 224 --base_lr 0.05 --batch_size 24
```
## Testing
To test the model, run the following command in the CMD.ipynb notebook:
```

!python3 TransUNet/test.py --dataset Synapse --cfg TransUNet/configs/swin_tiny_patch4_window7_224_lite.yaml --is_saveni --volume_path data/Synapse --output_dir output --max_epoch 150 --base_lr 0.05 --img_size 224 --batch_size 24
```
# Results Visualization
The code was missing the capability to visualize final results. Therefore, the open_nii_gz function was added to the code, which can visualize images, labels, and predictions. To visualize the results, the following code can be added after the testing command:

```
from TransUNet.utils.visualize import open_nii_gz
```
## visualize the first predicted image
open_nii_gz('output/test_volumes/volume-0000.nii.gz', 'output/test_niis/volume-0000.nii.gz')

### note : Main Parts of the Code
The following are the main parts of the code along with their subparts:

CMD.ipynb is used as terminal :D
trainer
train
test
results visualization (implemented by me, it was missing in the original code by the author)
Note
The original code was designed to run for 150 epochs on a Colab GPU, which takes around 6 hours to complete. 

## Dont use this code for self diagnosing 
