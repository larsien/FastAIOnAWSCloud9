Miniconda + FastAI + Jupyter notebook + Cloud9 on AWS
======
## Pre-requsites

#### AWS cloud9(t2.micro is not available because of memory limit. Use t2.small or above)

Resizing disk is needed. Default disk space is 8GB and this is totally not enough. I think 16GB is enough to run.
[link](https://docs.aws.amazon.com/cloud9/latest/user-guide/move-environment.html#move-environment-resize)

    ./resize.sh 16

Run disk resizing script in above link. And before running disk resizing, Cloud9 needs to set aws access key and secret key. You need configure this things.

    aws configure

#### your hands

## Script
    git clone https://github.com/fastai/fastai
    wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
    chmod a+x Miniconda3-latest-Linux-x86_64.sh 
    ./Miniconda3-latest-Linux-x86_64.sh 

Download dataset and unzip to "fastai/data/bulldozers/". check below movie.
<https://youtu.be/CzdWqFTmn0Y?t=939>

    unzip bulldoz.zip 
    
Activate python3 virtual env
    
    conda create -n fastaienv python=3.6 anaconda

Add uninstalled packages. Cloud9 has default python version2.7. So that you need to specify python.

    conda install -c anaconda bcolz
    conda update -n base conda
    python3 -m pip install opencv-python
    python3 -m pip install graphviz
    python3 -m pip install sklearn_pandas
    python3 -m pip install isoweek
    python3 -m pip install pandas_summary
    
## Run Jupyter notebook
    jupyter notebook --ip=0.0.0.0 --port=8080 --no-browser

Run <Code>Preview - Preview Running Application</Code> on Cloud9 then you can get accees link like below.

    http://*.vfs.cloud9.ap-southeast-1.amazonaws.com/
    
Add above port.(Below link is an example)
    
    http://*.vfs.cloud9.ap-southeast-1.amazonaws.com:8080/

In terminal, you can get access token. Insert the token to login. DONE!

## References
<https://medium.com/@GuruAtWork/fast-ai-lesson-1-7fc38e978d37>
<https://github.com/fastai/fastai/blob/master/README.md#installation-issues>
