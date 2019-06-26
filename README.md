# Mark RCNN Repo Setup

Install [Anaconda](https://docs.anaconda.com/anaconda/install/) for your OS from the different versions available

## Create Seperate Virtual Enviroment

1. Check conda is installed and in your PATH

    1. Open a terminal client.
    2. Enter ```conda -V``` into the terminal command line and press enter.
    3. If conda is installed you should see somehting like the following.
```python
$ conda -V 
conda 3.7.0
```

2. Check conda is up to date

    In the terminal client enter

```conda update conda```

   Upadate any packages if necessary by typing y to proceed

3. Create a virtual environment for your project

    In the terminal client enter the following where yourenvname is the name you want to call your environment, and replace x.x with the Python version you wish to use. (To see a list of available python versions first, type ```conda search "^python$"``` and press enter.)
```python
conda create -n yourenvname python=x.x anaconda
```
Download Mask-RCNN repository for GitHub - https://github.com/matterport/Mask_RCNN Press ```y``` to proceed. This will install the Python version and all the associated anaconda packaged libraries at ```“path_to_your_anaconda_location/anaconda/envs/yourenvname”```

4. Activate your virtual environment.

    To activate or switch into your virtual environment, simply type the following where yourenvname is the name you gave to your environement at creation.
```python
source activate yourenvname
```
For Windows

OR
```python
conda activate yourenvname
```
In Ubuntu

## Github Repo Download

1. Clone Mask-RCNN Repo
```python
git clone https://github.com/matterport/Mask_RCNN.git
```
2. Download pretrained model from here: [mask_rcnn_coco](https://github.com/matterport/Mask_RCNN/releases/download/v2.1/mask_rcnn_balloon.h5)


3. Move downloaded model to MASK_RCNN folder

4. Remove TensorFlow from that ```requirements.txt``` file because we want to use TensorFlow-GPU.

5. In terminal go to MASK_RCNN Folder and then type
```python
pip install –r requiments.txt
```
6. Mask-RCNN also requires cocoapi. To install cocoapi go to - [COCOAPI](https://github.com/philferriere/cocoapi)

7. Open: "cocoapi-master" folder
8. Go to: "PythonAPI" folder
9. Run in CMD:``` python setup.py build_ext install ```

## Setting Up For TensorFlow-GPU
1. Install NVIDIA Graphics Driver via apt-get

CUDA 9.0 requires NVIDIA driver version 384 or above. To install the driver, use apt-get instead of the CUDA runfile:
```python
sudo apt-get install nvidia-384 nvidia-modprobe
```
Reboot your computer and check if drivers are installed correctly or not using:  ```nvidia-smi```
```python
$ sudo apt-get --purge -y remove 'cuda*'
```
to remove previous installations
2. Install CUDA Toolkit 9.0 and cuDNN 7.0 as follows:

Download CUDA 9.0 deb version from [here](https://developer.nvidia.com/cuda-90-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=debnetwork).
And Run following commands from the terimal:
```python
sudo dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda
```
Set up the development environment by modifying the PATH and LD_LIBRARY_PATH variables, also add them to the end of bashrc file:
```python
export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
Download and install [cuDNN](https://developer.nvidia.com/rdp/cudnn-archive) for cuda9.0 by logging in to the website
```
pip install tensorflow-gpu==1.8
```
### Running Mask RCNN for Video
Download and place the video_demo.py and visualize_cv2.py in Mask_RCNN_Master folder
```
python video_demo.py 0
```
OR
```
python video_demo.py video.mp4
```
Your  Mask RCNN should work on GPU if everthing works correctly

