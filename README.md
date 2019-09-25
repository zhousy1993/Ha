# Ha
begin


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
