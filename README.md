# WSRFNet: Wavelet-Based Scale-Specific Recurrent Feedback Network for Diabetic Retinopathy Lesion Segmentation

## Code Environment
```bash
conda create -n WSRFNet python=3.8
conda activate WSRFNet
pip install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html
pip install -r requirements.txt
```

## Data Preparation
You can refer to the work  ['Automated lesion segmentation in fundus images with many-to-many reassembly of features'](https://github.com/CVIU-CSU/M2MRF-Lesion-Segmentation) [Pattern Recognition 2023] for the IDRID and DDR datasets. 

The download of the datasets can be found [here](https://github.com/CVIU-CSU/M2MRF-Lesion-Segmentation#results-and-models).

 The preparation of the datasets can be found [here](https://github.com/CVIU-CSU/M2MRF-Lesion-Segmentation#training-and-testing). 

 Then, reorganize the file structure of the test sets as follows and put the 'test_set' in the root directory of the code file.

 ```bash
├── test_set
│   ├── DDR
│   │   ├── annotations
│   │   └── image
│   └── IDRID
│       ├── annotations
│       └── image
 ```

## Inference
We use the same evaluation code as the ['Automated lesion segmentation in fundus images with many-to-many reassembly of features'](https://github.com/CVIU-CSU/M2MRF-Lesion-Segmentation) to evaluate the predicted segmentation maps.

We ensemble the aboved evaluation code into our code.

### Notice
The pretrained weights can be obtained by emailing me (xuanli@stu.hit.edu.cn) and promising that all code and pre-trained weights are intended for non-commercial use only and must not be used for any commercial purposes without explicit written permission. 

### IDRID

First, unzip the compressed files 'idrid_model.zip' into the checkpoint file 'idrid_model.pth'.

```bash
unzip idrid_model.zip
```
Then, test the model and save the predicted segmentation maps via '--vis_results'.

```bash
python test.py -d IDRID -p test_set/IDRID -c idrid_model.pth --vis_results
```

### DDR

First, unzip the compressed files 'ddr_model.zip' into the checkpoint file 'ddr_model.pth'.

```bash
unzip ddr_model.zip
```
Then, test the model and save the predicted segmentation maps via '--vis_results'.

```bash
python test.py -d DDR -p test_set/DDR -c ddr_model.pth --vis_results
```
