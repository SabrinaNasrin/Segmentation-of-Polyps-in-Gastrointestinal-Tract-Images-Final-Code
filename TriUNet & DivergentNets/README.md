
# Polyp Segmentation using TriUnet & DivergentNets

## 1) Platform
This code can be executed in google colab.

## 2) Package Dependencies:
1.)pyra_pytorch<br />
2.)segmentation_models_pytorch<br />
3.)ipykernel<br />
4.)albumentations<br />

```
!pip install pyra_pytorch
!pip install segmentation_models_pytorch
!pip install ipykernel
!pip install albumentations==1.0.3
```

## 4) Steps for training TriUnet:
```
!python /content/drive/MyDrive/DivergentNets/divergent-nets-main/tri_unet.py train \
    --num_epochs 200 \
    --train_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C1.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C2.csv\
    --val_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C3.csv /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/C4.csv \
    --test_CSVs /content/drive/MyDrive/DivergentNets/divergent-nets-main/dataset/Gridtesting.csv \
    --out_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/output_dir \
    --tensorboard_dir /content/drive/MyDrive/DivergentNets/divergent-nets-main/tensorboard_dir
```

## 5) Testing Divergentnets
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

## 6) Results
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/Unet/results/10.png?raw=true)
![alt text](https://github.com/SabrinaNasrin/Segmentation-of-Polyps-in-Gastrointestinal-Tract-Images-Final-Code/blob/main/Unet/results/9.png?raw=true)
