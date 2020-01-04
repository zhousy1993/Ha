# utils

# Tutorials
https://www.programiz.com/python-programming/first-program
https://www.runoob.com/w3cnote/python-func-decorators.html

# Create a bootable ubuntu 16.04 usb
https://vitux.com/how-to-create-a-bootable-usb-stick-from-the-ubuntu-terminal/

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

