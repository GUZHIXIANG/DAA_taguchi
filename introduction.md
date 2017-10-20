***********************************************************
*********** An introduction for the DAA program ***********
***********************************************************
*NOTE: Please read this introduction before launching DAA program*



# Development environment

・Ubuntu 12/14/16 LTS

・Python2.7.*


MULTIPLE VERSION CONEXISTENCE
***********************************************************

\# install Python2.* & Python3.*
*It is unnecessary if Python2 & 3 have been installed.*
`sudo apt-get install python2.7 python2.7-dev python3.5 python3.5-dev`

\# install compile environment
`sudo apt-get install build-essential libssl-dev libevent-dev libjpeg-dev libxml2-dev libxslt-dev`

install pip
`sudo apt-get install python-pip`

install virtualenv
*virtualenv is a tool to create isolated Python environments.*
`sudo pip install virtualenv`


install Python2.7 virtualenv
`virtualenv --no-site-packages -p /usr/bin/python2.7 ~/.venv/python2.7`

install Python3.5 virtualenv
`virtualenv --no-site-packages -p /usr/bin/python3.5 ~/.venv/python3.5`

install virtualenvwrapper
*virtualenvwrapper is a set of extensions to virtualenv tool, which
includes wrappers for creating and deleting virtual environments
and managing your development workflow.*
`sudo pip install virtualenvwrapper`

add the following to shell launch file (~/.bashrc)
`export WORKON_HOME=$HOME/.virtualenvs`
`export PROJECT_HOME=$HOME/Devel`
*Normally the virualenvwrapper.sh will be /usr/local/bin/virualenvwrapper.sh,
but it may be overridden with your current python environment.
Please type '$ which virualenvwrapper.sh' to find the file.*
`source /usr/local/bin/virualenvwrapper.sh`
then reload it
`$ source ~/.bashrc`

create a new Python2.7 virtualenv for DAA and switch to it
*command reference -- mkvirtualenv ENVNAME -p python_version*
`mkvirtualenv env_daa -p python2.7`

change working virtualenv to env_daa
*Type the following when the working virtualenv is diferent*
`workon env_daa`
***********************************************************



# Requirement

・numpy 1.6.1

・matplotlib 1.1.1

・scipy 0.9.0

・scikit-learn 0.10

・paver 1.2.4

・pyzmq 14.6.0

・ipython　3.2.1


\\PACKAGE INSTALLATION\\

*Make sure your Python is working on virtualenv of DAA, or typing '$ workon env_daa'.*

install package with spectic version into DAA virtualenv
*Do not type 'sudo' here, else packages will install into root environment.*
*command reference -- pip install PACKAGENAME==VERSION*
`pip install numpy==1.6.1 matplotlib==1.1.1 scipy==0.9.0 sckit-learn==0.10 paver==1.2.4 pyzmq==14.6.0 ipython==3.2.1`

*If you cannot install matplotlib as the issue 'ft2build.h no such file or directory ubuntu', try the following*
`sudo apt-get install libfreetype6 libfreetype6-dev`



# Sourcecode

create the workspace for DAA then go there
`mkdir ~/workspace`
`cd ~/workspace`

download DAA sourcecode from our gitlab or by usb flash drive
`git clone https://github.com/GUZHIXIANG/DAA_taguchi.git`

add the following to the shell startup file (~/.bashrc)
*command reference -- export PYTHONPATH=the DAA path*
`export PYTHONPATH=/home/gu/workspace/NPB_DAA_develop`


move to the DAA path and modify core amount
*You can check the core amount in your PC by typing 'htop'*
*htop is an ncursed-based process viewer *
*htop installation -- 'sudo apt-get install htop'*
`gedit ~/workspace/NPB_DAA_develop/IPCLUSTER.sh`
change the amout as below
`'ipcluster start -n 8' ---> 'ipcluster start -n YOUR_CORE_AMOUNT'`



# Launch DAA program
*Make sure your Python is working on virtualenv of DAA, or typing '$ workon env_daa'.*

open a new terminal to launch htop for monitering core running
`htop`

open a new terminal to launch ipcluster.sh for parallel computation
`sh ~/workspace/NPB_DAA_develop/HDP_HLM/SAMPLE2/IPCLUSTER.sh`

open a new terminal and move to /NPB_DAA_develop/HDP_HLM/SAMPLE2
`cd ~/workspace/NPB_DAA_develop/HDP_HLM/SAMPLE2`

reload shell launch file (~/.bashrc)
`source ~/.bashrc`

launch DAA program
`ipython startDAA.py`



# Result visualization
*Make sure your Python is working on virtualenv of DAA, or typing '$ workon env_daa'.*

move to the result folder named startDAA_result_n
*The whole results are saved in the startDAA_result_n folder, which is named with the maximal number existed*
`cd ~/workspace/NPB_DAA_develop/HDP_HLM/SAMPLE2/startDAA_result_[THE_MAXIMAL_NUMBER]`

launch summary.py to plot visual result
`ipython ../summary.py`


