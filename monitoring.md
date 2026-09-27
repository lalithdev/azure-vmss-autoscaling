\# Monitoring



\## Azure Monitor



Azure Monitor was used to monitor the performance of the Virtual Machine Scale Set.



\### Metric Monitored



The main metric used for autoscaling was:



\- Metric: Percentage CPU

\- Aggregation: Average

\- Time grain: 1 minute



\### Monitoring Process



1\. Opened the `vmss-autoscale-demo` Virtual Machine Scale Set.

2\. Opened the Monitoring/Metrics section.

3\. Selected the `Virtual Machine Host` metric namespace.

4\. Selected `Percentage CPU`.

5\. Selected `Average` aggregation.

6\. Observed CPU utilization of the VMSS instances.

7\. Used the CPU metric as the basis for autoscaling.



\### CPU Monitoring



The CPU metric was used to determine when the VMSS should scale out or scale in.



```text

&#x20;             Azure Monitor

&#x20;                  |

&#x20;            Percentage CPU

&#x20;                  |

&#x20;         +--------+--------+

&#x20;         |                 |

&#x20;      > 70%             < 30%

&#x20;         |                 |

&#x20;         v                 v

&#x20;     Scale Out          Scale In

&#x20;       +1                  -1

