\# Deployment



\## Azure VMSS Deployment



The Azure Virtual Machine Scale Set was deployed using the Azure Portal.



\### Resource Group



Resource Group:

`VMSS-Autoscale-RG`



\### Virtual Machine Scale Set



VMSS Name:

`vmss-autoscale-demo`



\### Operating System



Ubuntu 24.04 LTS



\### VM Size



Standard B2s v2



\### Initial Instance Count



2 instances



\### Instance Limits



\- Minimum: 2

\- Maximum: 5

\- Default: 2



\### Deployment Steps



1\. Created the Azure Resource Group.

2\. Created the Virtual Machine Scale Set.

3\. Selected Ubuntu 24.04 LTS as the operating system.

4\. Configured the VM size as Standard B2s v2.

5\. Set the initial instance count to 2.

6\. Configured autoscaling based on Percentage CPU.

7\. Configured scale-out and scale-in rules.

8\. Configured the Network Security Group with SSH access.

9\. Connected to the Linux VM using SSH.

10\. Installed the `stress` utility for CPU load testing.

11\. Monitored CPU utilization using Azure Monitor.

12\. Verified the VMSS instances and autoscale configuration.



\## Deployment Result



The VM Scale Set was successfully deployed with two initial instances and configured for CPU-based autoscaling.

