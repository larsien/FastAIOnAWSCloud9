Miniconda + FastAI + Jupyter notebook + cloud9 on AWS
======
## Pre-requsites

#### AWS cloud9(t2.micro is not available because of memory limit)

Resizing disk is needed. Default disk space is 8GB and this is totally not enough.
[link](https://docs.aws.amazon.com/cloud9/latest/user-guide/move-environment.html#move-environment-resize)

Run disk resizing script above link. And before running disk resizing, Cloud9 needs to set aws access key and secret key. You need configure this things.

    aws configure

#### your hands

## Script
    curl 'https://storage.googleapis.com/kaggle-datasets/13827/18639/Train.zip?GoogleAccessId=web-data@kaggle-161607.iam.gserviceaccount.com&Expires=1547291879&Signature=TLjlp1VaW%2BLa7czig6a0MemhYiPZfssuEbHqCQbd9sKWI90p0irh8BBHAshkw7EG2Azrgqpz1J86d3%2FYodvZn3VVp4d5nipUfmmfj4THXuXgPsKwzqT%2FI4GrOTtW8IVeKE2%2Fv2AxXuWwddWx5xJ%2B5StHQqXwpki4fDcHmdGqaUCvnlVk%2BCY7NLJitmOcFoD8e5pz3Oy%2B%2Br4TIbxoH4FbGP4akiVwqOpXqUKY1754HYatoupfnfR1q3%2FiXDDVJQ9L7uEeUL3wEELNKpj8wEhcxyhWfsspDVoEPbMmgU9X3mmuRLmUCy2X2sj%2BZTIKTLJu9VliKmy6HEdepHHI%2Fbcdmw%3D%3D' -H 'Connection: keep-alive' -H 'Upgrade-Insecure-Requests: 1' -H 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8' -H 'Referer: https://www.kaggle.com/' -H 'Accept-Encoding: gzip, deflate, br' -H 'Accept-Language: en-US,en;q=0.9,ko;q=0.8' --compressed -o bulldoz.zip

    sudo apt-get install unzip
    unzip bulldoz.zip
    git clone https://github.com/fastai/fastai
    wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
    chmod a+x Miniconda3-latest-Linux-x86_64.sh 
    ./Miniconda3-latest-Linux-x86_64.sh 
    
Activate python3 virtual env
    
    conda create -n fastaienv python=3.6 anaconda
    
Add uninstalled packages. Cloud9 has default python version2.7. 

    conda install -c anaconda bcolz
    conda update -n base conda
    python3 -m pip install opencv-python
    python3 -m pip install graphviz
    python3 -m pip install sklearn_pandas
    python3 -m pip install isoweek
    python3 -m pip install pandas_summary
    
## Run Jupyter notebook
    jupyter notebook --ip=0.0.0.0 --port=8080 --no-browser

Run Preview on Cloud9 and add above port.(Below link is an example)

    http://*.vfs.cloud9.ap-southeast-1.amazonaws.com:8080/tree/workspace_name

