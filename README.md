# Ha
begin


# Killing all python processes
for i in $(sudo lsof /dev/nvidia0 | grep python  | awk '{print $2}' | sort -u); do kill -9 $i; done

# Stop all processes using CUDA wit lsof
lsof /dev/nvidia*
