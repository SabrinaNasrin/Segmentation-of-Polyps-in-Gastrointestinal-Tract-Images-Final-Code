
# Polyp Segmentation using TriUnet & DivergentNets

## 1) Platform
This code can be executed in google colab.

## 2) Package Dependencies:
1.)pyra_pytorch<br />
2.)segmentation_models_pytorch<br />
3.)ipykernel<br />
4.)albumentations<br />
5.)pytorch <br />
6.)torchvision <br />
7.)tqdm<br/>
8.)pandas<br />
9.)numpy<br />
10.)torchsummary<br />

```
!pip install pyra_pytorch
!pip install segmentation_models_pytorch
!pip install ipykernel
!pip install albumentations==1.0.3
```
## 3) Datasets:
PolypGen dataset is used for training. The link to get the dataset is given below:<br/>
https://www.synapse.org/#!Synapse:syn26376620

Kvasir-Seg dataset is used for testing.  The link to get the dataset is given below:<br/>
https://datasets.simula.no/kvasir-seg/

## 4) Steps for training TriUnet:
```
!python  /content/drive/MyDrive/DivergentNets/divergent-nets-main/tri_unet.py train \
    --num_epochs 200 \
    --device_id 0  \
    --train_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C1.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C2.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C3.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C4.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C5.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C6.csv \
    --val_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq1.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq2.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq3.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq4.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq5.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq6.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/seq7.csv\
    --test_CSVs  /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/Kvasir-seg.csv \
    --tensorboard_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/tensorboard_dir \
    --out_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir 
```
To train other models, you have to replace tri_unet.py with one of the follwings: <br />
unet_plusplus.py<br />
deeplabv3.py<br />
deeplabv3_plusplus.py<br />

## 5) Steps for testing TriUnet:
```
!python /content/drive/MyDrive/DivergentNets/divergent-nets-main/tri_unet.py test \
    --best_checkpoint_name /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir/tri_unet.py/checkpoints/best_checkpoint_TriUnet.pth \
    --num_epochs 200 \
    --train_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C1.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C2.csv\
    --val_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C3.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C4.csv \
    --test_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/Gridtesting.csv \
    --out_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir \
    --tensorboard_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/tensorboard_dir
```

## 6) Prediction images for TriUnet
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/TriUNet%20%26%20DivergentNets/Prediction%20Images%20for%20TriUnet/test_0.jpg?raw=true)
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/TriUNet%20%26%20DivergentNets/Prediction%20Images%20for%20TriUnet/test_1.jpg?raw=true)

## 7) Testing Divergentnets
```
!python /content/drive/MyDrive/DivergentNets/divergent-nets-main/inference_from_divergentNets.py \
    --input_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/Testing1 \
    --output_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/GridTestingDivergentNets \
    --chk_paths \
    /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir/tri_unet.py/checkpoints/best_checkpoint_Deeplabv3.pth\
    /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir/tri_unet.py/checkpoints/best_checkpoint_Depplabv3_plusplus.pth\
    /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir/tri_unet.py/checkpoints/best_checkpoint_FPN.pth \
    /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir/tri_unet.py/checkpoints/best_checkpoint_TriUnet.pth \
    /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir/tri_unet.py/checkpoints/best_checkpoint_unet_plusplus.pth
 ```
## 8) Result for divergentnet
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/TriUNet%20%26%20DivergentNets/prediction%20images%20for%20divergentnet/divergentnet%20result.jpg?raw=true)

## 9) Enhancements
We used color correction, specular removal and checked IOU with different sizes of images (image pyramid).<br/>
The codes for this part is in ```Enhancements.ipynb``` 

The results for color correction and specular removal can be seen in ```Enhancements.ipynb``` <br/>
The results for different size of images (image pyramid) is shown below:<br/>

![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/TriUNet%20%26%20DivergentNets/image-pyramid/image%20pyramid.jpg?raw=true)

## 10) Citation
```
@inproceedings{divergentNets,
  title={DivergentNets: Medical Image Segmentation by Network Ensemble},
  author={Thambawita, Vajira and Hicks, Steven A. and Halvorsen, P{\aa}l and Riegler, Michael A.},
  booktitle={Proceedings of the 3rd International Workshop and Challenge on Computer Vision in Endoscopy (EndoCV 2021)
co-located with with the 17th IEEE International Symposium on Biomedical Imaging (ISBI 2021)},
  year={2021}
}
```
Github link for the code ```https://github.com/vlbthambawita/divergent-nets```









