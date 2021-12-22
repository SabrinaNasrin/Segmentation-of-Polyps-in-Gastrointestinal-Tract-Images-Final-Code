# Making the CSV files of the dataset
Step 1: Install natsort
```
pip install natsort
```
Step 2: Run the example code given below:
```python
import os
import pandas as pd
import numpy as np
import natsort

BASE_DIR = '/content/drive/MyDrive/DivergentNets/divergent-nets-main/Kvasir-SEG/'
images_folder = BASE_DIR+'images/'
Mask_annotation = BASE_DIR+'masks/'
files_in_train =  natsort.natsorted(os.listdir(images_folder),reverse=False)
print(files_in_train)

s = files_in_train
i = 0

for n in files_in_train:
    s[int(i)] = images_folder + files_in_train[int(i)]
    i=i+1
#print(s)

files_in_annotated = natsort.natsorted(os.listdir(Mask_annotation),reverse=False)
print(files_in_annotated)
t = files_in_annotated
j = 0

for k in files_in_annotated:
    t[int(j)] = Mask_annotation + files_in_annotated[int(j)]
    j=j+1
print(len(t))
df = pd.DataFrame()
df['image_path']=s
df['mask_path']=t

df.to_csv('Kvasir-seg.csv', header=('image_path','mask_path'))
```

