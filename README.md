*NOTE: Please read this introduction before launching DAA program*


# Development environment

・Ubuntu 12/14/16 LTS<br>
・Python2.7.*


## Multipe version conexistence

install Python2.* & Python3.*<br>
*It is unnecessary if Python2 & 3 have been installed.*<br>
`sudo apt-get install python2.7 python2.7-dev python3.5 python3.5-dev`<br>
<br>
install compile environment<br>
`sudo apt-get install build-essential libssl-dev libevent-dev libjpeg-dev libxml2-dev libxslt-dev`<br>
<br>
install pip<br>
`sudo apt-get install python-pip`<br>
<br>
install virtualenv<br>
*virtualenv is a tool to create isolated Python environments.*<br>
`sudo pip install virtualenv`<br>
<br>
install Python2.7 virtualenv<br>
`virtualenv --no-site-packages -p /usr/bin/python2.7 ~/.venv/python2.7`<br>
<br>
install Python3.5 virtualenv<br>
`virtualenv --no-site-packages -p /usr/bin/python3.5 ~/.venv/python3.5`<br>
<br>
install virtualenvwrapper<br>
*virtualenvwrapper is a set of extensions to virtualenv tool, which
includes wrappers for creating and deleting virtual environments
and managing your development workflow.*<br>
`sudo pip install virtualenvwrapper`<br>
<br>
add the following to shell launch file<br>
`echo "export WORKON_HOME=$HOME/.virtualenvs" >> ~/.bashrc`<br>
`echo "export PROJECT_HOME=$HOME/Devel" >> ~/.bashrc`<br>
*Normally the virualenvwrapper.sh will be /usr/local/bin/virualenvwrapper.sh,
but it may be overridden with your current python environment.
Please type* `$ which virualenvwrapper.sh` *to find the file.*<br>
`echo "source /usr/local/bin/virualenvwrapper.sh" >> ~/.bashrc`<br>
then reload it<br>
`source ~/.bashrc`<br>
<br>
create a new Python2.7 virtualenv for DAA and switch to it<br>
*command reference* `mkvirtualenv ENVNAME -p PYTHON_VERSION`<br>
`mkvirtualenv env_daa -p python2.7`<br>
<br>
change working virtualenv to env_daa<br>
*Type the following when the working virtualenv is diferent*<br>
`workon env_daa`<br>




# Requirement

・numpy 1.6.1<br>
・matplotlib 1.1.1<br>
・scipy 0.9.0<br>
・scikit-learn 0.10<br>
・paver 1.2.4<br>
・pyzmq 14.6.0<br>
・ipython　3.2.1


## Package installation
*Make sure your Python is working on virtualenv of DAA, or typing* `workon env_daa`.<br>

install package with spectic version into DAA virtualenv<br>
*Do not type 'sudo' here, else packages will install into root environment.*<br>
*command reference* `pip install PACKAGENAME==VERSION`<br>
`pip install numpy==1.6.1 matplotlib==1.1.1 scipy==0.9.0 sckit-learn==0.10 paver==1.2.4 pyzmq==14.6.0 ipython==3.2.1`<br>
<br>
*If you cannot install matplotlib as the issue 'ft2build.h no such file or directory ubuntu', try the following*<br>
`sudo apt-get install libfreetype6 libfreetype6-dev`<br>



# Sourcecode

create the workspace for DAA then go there<br>
`mkdir ~/workspace`<br>
`cd ~/workspace`<br>
<br>
download DAA sourcecode from our gitlab or by usb flash drive<br>
`git clone https://github.com/GUZHIXIANG/DAA_taguchi.git`<br>
<br>
add the following to the shell launch file<br>
*command reference* `export PYTHONPATH=YOUR_DAA_PATH`<br>
`echo "export PYTHONPATH=/home/gu/workspace/NPB_DAA_develop" >> ~/.bashrc`<br>
<br>
move to the DAA path and modify core amount<br>
*You can check the core amount in your PC by typing* `htop`<br>
*htop is an ncursed-based process viewer*<br>
*htop installation* `sudo apt-get install htop`<br>
`gedit ~/workspace/NPB_DAA_develop/IPCLUSTER.sh`<br>
change the amout as below<br>
`'ipcluster start -n 8' ---> 'ipcluster start -n YOUR_CORE_AMOUNT'`<br>



# Launch DAA program
*Make sure your Python is working on virtualenv of DAA, or typing* `workon env_daa`.<br>
<br>
open a new terminal to launch htop for monitering core running<br>
`htop`<br>
<br>
open a new terminal to launch ipcluster.sh for parallel computation<br>
`sh ~/workspace/NPB_DAA_develop/HDP_HLM/SAMPLE2/IPCLUSTER.sh`<br>
<br>
open a new terminal and move to /NPB_DAA_develop/HDP_HLM/SAMPLE2<br>
`cd ~/workspace/NPB_DAA_develop/HDP_HLM/SAMPLE2`<br>
<br>
reload shell launch file (~/.bashrc)<br>
`source ~/.bashrc`<br>
<br>
launch DAA program<br>
`ipython startDAA.py`<br>



# Result visualization
*Make sure your Python is working on virtualenv of DAA, or typing* `workon env_daa`.<br>
<br>
move to the result folder named startDAA_result_n<br>
*The whole results are saved in the startDAA_result_n folder, which is named with the maximal number existed*<br>
`cd ~/workspace/NPB_DAA_develop/HDP_HLM/SAMPLE2/startDAA_result_[THE_MAXIMAL_NUMBER]`<br>
<br>
launch summary.py to plot visual result<br>
`ipython ../summary.py`<br>

<br>
<br>
<br>


*****************************************
# Original README.md

## Nonparametric Bayesian Double Articulation Analyzer

This is a Python implementation for Nonparametric Bayesian Double Articulation Analyzer (NPB-DAA). The NPB-DAA can directly acquire language and acoustic models from observed continuous speech signals.

This generative model is called hiererichel Dirichlet process hidden language model (HDP-HLM), which is obtained by extending the hierarchical Dirichlet process hidden semi-Markov model (HDP-HSMM) proposed by Johnson et al. An inference procedure for the HDP-HLM is derived using the blocked Gibbs sampler originally proposed for the HDP-HSMM.

## Description
・NPB_DAA/README - There is a NPB-DAA tutorial in PDF.(In Japanese. English version is coming soon.)

・NPB_DAA/HDP-HSMM - Python Library for HDP-HSMM. You can get it at [ https://github.com/mattjj/pyhsmm ]. (Please check this VERSION at README)

・NPB_DAA/HDP-HLM - Python code for NPB-DAA

## Requirement

・Ubuntu 12.04.5 LTS

`sudo apt-get install`

・python 2.7.3

・numpy 1.6.1

・matplotlib 1.1.1rc

・scipy 0.9.0

・scikit-learn 0.10

`sudo pip install`

・Paver 1.2.4

・pyzmq==14.4.0/14.5.0/14.6.0 (14.6.0)

・ipython　3.2.1

## Usage
前のバージョンのものですが，勉強会の資料があります．
ディレクトリの構成が変更されていますので，よろしく，おねがいします．


## Troubleshooting
If you are in trouble, please look at this document. You can get information about environment operability confirmed and actions on error occuring often.
  [Troubleshooting document](https://docs.google.com/document/d/1fwcnwNEZNvc1vVZvyRJsMtPdC_FNAtY9S3dyS5CVxZQ/edit?usp=sharing)

## References
・Taniguchi, Tadahiro, Shogo Nagasaka, and Ryo Nakashima. [Nonparametric Bayesian double articulation analyzer for direct language acquisition from continuous speech signals](http://ieeexplore.ieee.org/document/7456220/?arnumber=7456220), 2015.

・Matthew J. Johnson and Alan S. Willsky. [Bayesian Nonparametric Hidden Semi-Markov Models](http://www.jmlr.org/papers/volume14/johnson13a/johnson13a.pdf). Journal of Machine Learning Research (JMLR), 14:673–701, 2013.

## Authors
Tadahiro Taniguch, Ryo Nakashima, Nagasaka Shogo, Tada Yuki, Kaede Hayashi.

### License
* MIT
    * see LICENSE
*****************************************
