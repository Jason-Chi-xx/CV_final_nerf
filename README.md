# CV_final_nerf

the task three of the CV final project

To reproduce this work, you should follow these steps:

**First**, clone the nerf-pytorch repository:

```bash
git clone https://github.com/yenchenlin/nerf-pytorch.git
cd nerf-pytorch
pip install -r requirements.txt
```

**Second**, clone the llff repository to transform your data into llff-form:

````
git clone https://github.com/Fyusion/LLFF.git
cd LLFF
python imgs2poses.py path/to/dataset
````

After that, you will get a new file named poses_bound in your dataset directory

**Third**, make your own dataset and put it into nerf_llff_data directory as follows (take blueball as an example):

````
├── configs                                                                                                       
│   ├── ...                                                                                     
│                                                                                               
├── data                                                                                                                                                                                                       
│   ├── nerf_llff_data                                                                                                  
│   │   └── fern                                                                                                                             
│   │   └── blueball  # your own llff-form dataset                                                                                  
|   |   └── ...
|   ├── nerf_synthetic
|   |   └── lego
|   |   └── ship    # downloaded synthetic dataset
|   |   └── ...
````

**Fourth**, put the blueball.txt under the configs directory. 

**Fifth**, run the downsample.py to downsample the data in order to train sucessfully:

````
python downsample.py --data_dir path/to/data --n 8 --save_dir path/to/save
````

**Sixth**, training:

```bash
python run_nerf.py --config configs/blueball.txt
```

**Notice** : 

 	The version of nerf-pytorch is quite old so it may encounter lots of problems. Thers is a little point that requires attention. That is if your image suffix is ".png", you may get error message from line 111 in nerf-pytorch/load_llff.py, so you'd better use other suffix like ".jpg" or "jpeg" to avoid it. 

**checkpoints link** : 

链接: https://pan.baidu.com/s/15EsG1j4lV1ILBJaCkcvL7A?pwd=n951 提取码: n951 
