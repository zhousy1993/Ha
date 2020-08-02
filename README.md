# utils

# Tutorials
https://www.programiz.com/python-programming/first-program
https://www.runoob.com/w3cnote/python-func-decorators.html

# Create a bootable ubuntu 16.04 usb
https://vitux.com/how-to-create-a-bootable-usb-stick-from-the-ubuntu-terminal/

# install nvidia graphic drivers on ubuntu16.04
https://tech.amikelive.com/node-731/how-to-properly-install-nvidia-graphics-driver-on-ubuntu-16-04/

# all cuda version & installation tutorial
https://tech.amikelive.com/node-859/installing-cuda-toolkit-9-2-on-ubuntu-16-04-fresh-install-install-by-removing-older-version-install-and-retain-old-version/#fresh-install

https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/

# cuda9.2 runfile

https://developer.nvidia.com/cuda-92-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=runfilelocal

export PATH=/usr/local/cuda-9.2/bin${PATH:+:${PATH}}

export LD_LIBRARY_PATH=/usr/local/cuda-9.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

# try to launch anaconda-navigator

source /home/zhousy/anaconda3/bin/activate

source ~/anaconda3/bin/activate root
anaconda-navigator

# add anaconda python path to the bashrc file

vi ~/.bashrc

export PATH="$PATH:/home/username/anaconda3/bin"

:wq

source ~/.bashrc

# Killing all python processes
for i in $(sudo lsof /dev/nvidia0 | grep python  | awk '{print $2}' | sort -u); do kill -9 $i; done

# Stop all processes using CUDA wit lsof
lsof /dev/nvidia*

# Set GPU power

You’ll want to make /usr/bin/nvidia-persistenced and /usr/bin/nvidia-smi able to be run as sudo without a password.

Then to query your power limit:

sudo nvidia-smi -q -d POWER

And to set it

sudo nvidia-smi -pl (base power limit+11)

And add that to a shell script that runs at startup. (This is why we made those able to run sudo without a password)

If you have multiple GPUs:

sudo nvidia-smi -i 0 -pl (Power Limit) GPU1
sudo nvidia-smi -i 1 -pl (Power Limit) GPU2

# Tensorboard

$ tensorboard --logdir='./logs' --port=6006

http://localhost:6006/ 

cd /home/zsy/PycharmProjects/tensorboardX

tensorboard --logdir=runs

localhost:   # in broser

https://github.com/lanpa/tensorboardX/blob/master/docs/tutorial.rst

AttributeError: 'module' object has no attribute 'FileWriter'

I saw there is some api change, probably to do with tf 2.0. This is working for me in tf 2.0:

train_writer = tf.summary.create_file_writer('./logs/1/train')

# TypeError: __init__() got an unexpected keyword argument 'pipeline'

python setup.py develop(In your project directory)

# Create soft links

ln -s source/links object/links


# Github push

1.git init

2.git config user.name "someone"

3.git config user.email "someone@someplace.com"

4.git add *

5.git commit -m "some init msg"

git init

git config user.name "zhousy1993"

git config user.email "zhousiyao1993@gmail.com"

git add *

git commit -m "initial commit"

git push origin master

# Problem of login loop after Ubuntu update

1. ctrl + alt + F3

2. sudo service lightdm stop  # for the problem of exit X server

3. cd ~/Downloads 

4. ./ runfile.run  # may use chmod +x ./ runfile.run

5. vi /etc/modprobe.d/blacklist-nouneau.conf  # for the problem of unable to load the kernel module 'nvidia.ko'

blacklist nouveau

blacklist lbm-nouveau

options nouveau modeset=0

alias nouveau off

alias lbm-nouveau off

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf

update-initramfs -u

reboot

6. sudo service lightdm start

# Install teamviewer

use gdebi to install, before installing gdebi, open software update in ubuntu setting follow this 

https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa

sudo apt install gdebi

sudo gdebi teamviewer_.deb

# mount the disk for ubuntu

https://medium.com/@sh.tsang/partitioning-formatting-and-mounting-a-hard-drive-in-linux-ubuntu-18-04-324b7634d1e0
