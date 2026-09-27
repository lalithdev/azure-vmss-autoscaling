\# Autoscaling Configuration



\## Azure VMSS Autoscale



The Virtual Machine Scale Set `vmss-autoscale-demo` was configured with CPU-based autoscaling.



\### Instance Limits



\- Minimum instances: 2

\- Maximum instances: 5

\- Default instances: 2



\### Scale-Out Rule



When the average Percentage CPU is greater than 70%:



\- Operation: Increase instance count

\- Change: +1 instance



\### Scale-In Rule



When the average Percentage CPU is less than 30%:



\- Operation: Decrease instance count

\- Change: -1 instance



\### Autoscale Flow



```text

&#x20;             Percentage CPU

&#x20;                    |

&#x20;         +----------+----------+

&#x20;         |                     |

&#x20;      CPU > 70%             CPU < 30%

&#x20;         |                     |

&#x20;         v                     v

&#x20;     Scale Out             Scale In

&#x20;        +1                    -1

&#x20;         |                     |

&#x20;         v                     v

&#x20;  Maximum = 5            Minimum = 2

