# utils

# Tutorials
https://www.programiz.com/python-programming/first-program
https://www.runoob.com/w3cnote/python-func-decorators.html

# Create a bootable ubuntu 16.04 usb
https://vitux.com/how-to-create-a-bootable-usb-stick-from-the-ubuntu-terminal/

# all cuda version & installation tutorial
https://tech.amikelive.com/node-859/installing-cuda-toolkit-9-2-on-ubuntu-16-04-fresh-install-install-by-removing-older-version-install-and-retain-old-version/#fresh-install

https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/


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

# TypeError: __init__() got an unexpected keyword argument 'pipeline'

python setup.py develop(In your project directory)

# Create soft links

ln -s source/links object/links

