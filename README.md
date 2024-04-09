# adlcv_project

Code base for CubeDETR: End-to-End 3D Object Detection with Transformers project for the class 'Advance Deep Learning for Computer Vision' at DTU


# Installation and setups
Clone this repo and fetch the submodules:

`git submodule update --init --recursive`

## Environment
For now, inspired in the installation guide for MonoDETR

## 1. Create a conda environment
```bash
conda create -n adlcv_project python=3.8
conda activate adlcv_project
```
## 2. Load HPC modules
What works for me (iony) is to load the following modules:
* `module load cuda/11.8`
* `module load gcc` 
* `module load nvidiamodulusbase/pytorch-1.13.0-python-3.8.16`

This are lthemodules I had loaded when manged to make it work, by loading the modules above:
1) latex/TeXLive19(default)
2) gcc/10.3.0-binutils-2.36.1(default)
3) cuda/11.8
4) gcc/11.3.0-binutils-2.38 <aL>
5) ninja/1.11.1 <aL>
6) doxygen/1.9.2 <aL>
7) cmake/3.25.2 <aL>
8) cudnn/v8.3.2.44-prod-cuda-11.X <aL>
9) ffmpeg/4.4.2 <aL>
10) intel/2023.0.0.mkl <aL>
11) nvidiamodulusbase/pytorch-1.13.0-python-3.8.16

## 3. Data
### MonoDETR
1. set the absolute path to the dataset in the `configs/monodetr.yaml` file, in the filed `dataset/root_dir`
2. Inside 'kitti_data/' unzip the `data_prep/ImageSets.zip` file
3. Download **_this_** [KITTI](http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=3d) dataset from the official website  store it in a folder (here named 'kitti_data/') (WARNING: Watch out for size limits, ask for scratch space from HPC)
   1. Download (left) color images, calibration and labels zip files
   <!-- #TODO: include code for unzipping in the right directory name  -->
        ```bash
        wget https://s3.eu-central-1.amazonaws.com/avg-kitti/data_object_image_2.zip -P kitti_data/
        ```
   2. Unzip the files
        ```bash
        unzip kitti_data/data_object_image_2.zip -d kitti_data/
        ```
4. The content of the 'kitti_data/' folder should look like this:
```
kitti_data/
├── ImageSets/
├── training/
├── testing/
```

## Requirements
Install MonoDETR requirements
conda requirements
```bash
conda install pytorch torchvision pytorch-cuda=11.8 -c pytorch -c nvidia
```

```bash
pip install -r models/monoDETR/requirements.txt
```