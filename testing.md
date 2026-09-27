\# Testing



\## VMSS Autoscaling Testing



The autoscaling configuration was tested by generating CPU load on the Linux VM.



\### CPU Load Test



The `stress` utility was installed on the Ubuntu VM using:



```bash

sudo apt update

sudo apt install -y stress

