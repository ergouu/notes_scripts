#  Sovle some OS problem

## unmet error

It happens when apt-get installation process was interupted. 

$ sudo apt --fix-broken install

$ sudo apt-get update

$ sudo apt-get upgrade


## pip install met "Retry" problem

add index by usering:

$ pip(3) install --index https://pypi.mirrors.ustc.edu.cn/simple/ THE_PACKAGE_YOU_WANA_INSTALL
