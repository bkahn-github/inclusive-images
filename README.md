# Kaggle Inclusive Images Solution

## Instructions

### Step 1: Start a Pytorch Deeplearing VM

### Step 2: Reserve a Static External IP Address

### Step 3: Create an Ingress Firewall

Source IP Range: `0.0.0.0/0`  
Port Number: `tcp:5000`

### Step 4: SSH into Instance

`gcloud compute ssh [user]@[instance]`

## Use Python3.6 or Conda

### Python3.6:

#### Step 1: Install python 3.6

Install required build tools

`sudo apt-get update && sudo apt-get upgrade`  
`sudo apt-get install -y make build-essential libssl-dev zlib1g-dev`  
`sudo apt-get install -y libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm`  
`sudo apt-get install -y libncurses5-dev  libncursesw5-dev xz-utils tk-dev`

Get python 3.6

`wget https://www.python.org/ftp/python/3.6.4/Python-3.6.4.tgz`  
`tar xvf Python-3.6.4.tgz`  
`cd Python-3.6.4`

Build python

`./configure --enable-optimizations`  
`make -j8`  
`sudo make altinstall`  
`cd ..`

#### Step 2: Create virtualenv

`virtualenv -p python3.6 tgs`  
`source tgs/bin/activate`

### Conda:

#### Step 1: Get Conda

`curl -O https://repo.anaconda.com/archive/Anaconda3-5.3.0-Linux-x86_64.sh`

`bash Anaconda3-5.3.0-Linux-x86_64.sh`

Follow the prompts, then restart

### Step 7: Clone Repo

`git clone https://github.com/bkahn-github/inclusive-images.git`  
`cd inclusive-images`  
`pip install -r requirements.txt`  Or `conda env create -f environment.yml`  
`cd ..`


### Step 8: Config Jupyter

`jupyter notebook --generate-config`  
`vim /home/kaggle/.jupyter/jupyter_notebook_config.py`

And add this to the config file:

```
c = get_config()  
c.NotebookApp.ip = '*'  
c.NotebookApp.open_browser = False  
c.NotebookApp.port = 5000  

```

### Step 9: Run Python3.6 or Conda in kernel

`python -m ipykernel install --user --name=kaggle`

### Step 10: Setup Kaggle API

`mkdir .kaggle`  
`cd .kaggle`  
`vim kaggle.json`

Add your kaggle api key

### Step 11: Download Data

`mkdir inclusive-images`  
`cd inclusive-images`  
`kaggle competitions download -c inclusive-images-challenge`

`pip install awscli`  

0-9 and a-f  
`aws s3 --no-sign-request cp s3://open-images-dataset/tar/train_0.tar.gz train`   
`tar -xzf train_0.tar.gz`

### Step 12: Run jupyter lab

`jupyter lab`

## Author

Bilal Khan (https://bilal.software)
