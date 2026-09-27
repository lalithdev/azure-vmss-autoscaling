\# VMSS Autoscale Commands



\## 1. Connect to the Azure VM using SSH



From Windows CMD:



```cmd

cd %USERPROFILE%\\Downloads

ssh -i vmss-key.pem azureuser@20.205.35.99

```



\## 2. Update Ubuntu packages



```bash

sudo apt update

```



\## 3. Install stress utility



```bash

sudo apt install -y stress

```



\## 4. Generate CPU Load



```bash

stress --cpu 2 --timeout 600

```



This command generates CPU load on the Linux VM for 600 seconds.



\## 5. Check CPU Load



The CPU utilization can be monitored from Azure Portal using:



\*\*VMSS → Monitoring → Metrics → Percentage CPU\*\*



\## 6. Autoscale Configuration



The project uses the following autoscale rules:



```text

CPU > 70%  → Scale Out → Increase instances by 1



CPU < 30%  → Scale In  → Decrease instances by 1

```



Instance limits:



```text

Minimum: 2

Default: 2

Maximum: 5

```



\## 7. Verify VMSS Instances



The Azure Portal VMSS overview can be used to verify the number of running instances after autoscaling.



