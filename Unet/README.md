
# Polyp Segmentation using Unet

 the Dataset CVC-612 can be downloaded from <a href="https://www.dropbox.com/s/p5qe9eotetjnbmq/CVC-ClinicDB.rar?dl=0"> here </a>

## 1) Software Dependencies:
1.) Python version 3.8.12<br />
2.) Pip version 21.2.2<br />

## 2) Python Package Dependencies:
1.)matplotlib==3.2.2<br />
2.)numpy==1.21.2<br />
3.)tensorflow==2.3.0<br />
4.)opencv-python==4.2.0.34<br />
5.)tqdm==4.62.3<br />
6.)scikit-learn==1.0.1<br />

## 3) Create environment for UNet
- Create conda environment with following command conda create -n unet python=3.8
- Activate environment with following command conda activate unet
- Install above mentioned package dependencies
 
## 4) Execution Steps:
1)Run data.py<br />
2)Run model.py

## 5) Training and Testing
1) Run train.py for training
2) Create a folder "results" in the same folder as the project
3) Run predict.py for testing

## 6) Results
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/Unet/results/10.png?raw=true)
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/Unet/results/9.png?raw=true)


## 7) Citation
https://github.com/nikhilroxtomar/Polyp-Segmentation-using-UNET-in-TensorFlow-2.0
