\# Architecture



\## Azure VMSS Autoscale Architecture



```text

&#x20;                   Azure Resource Group

&#x20;                   VMSS-Autoscale-RG

&#x20;                           |

&#x20;                           v

&#x20;               +-----------------------+

&#x20;               | Azure VM Scale Set    |

&#x20;               | vmss-autoscale-demo   |

&#x20;               +-----------+-----------+

&#x20;                           |

&#x20;                 +---------+---------+

&#x20;                 |                   |

&#x20;                 v                   v

&#x20;            VM Instance 1       VM Instance 2

&#x20;            Ubuntu 24.04        Ubuntu 24.04

&#x20;                 |                   |

&#x20;                 +---------+---------+

&#x20;                           |

&#x20;                           v

&#x20;                    Azure Monitor

&#x20;                           |

&#x20;                    Percentage CPU

&#x20;                           |

&#x20;                           v

&#x20;                   Azure Autoscale

&#x20;                    /          \\

&#x20;                   /            \\

&#x20;            CPU > 70%          CPU < 30%

&#x20;                |                  |

&#x20;                v                  v

&#x20;            Scale Out           Scale In

&#x20;               +1                  -1

&#x20;                |                  |

&#x20;                v                  v

&#x20;         Maximum 5            Minimum 2



\## Architecture Components



\- Azure Resource Group: `VMSS-Autoscale-RG`

\- Virtual Machine Scale Set: `vmss-autoscale-demo`

\- Operating System: Ubuntu 24.04

\- Monitoring: Azure Monitor

\- Metric: Percentage CPU

\- Autoscale: CPU-based scaling



\## Scaling Flow



\### Scale Out



CPU > 70% → Increase instance count by 1 → Maximum 5 instances



\### Scale In



CPU < 30% → Decrease instance count by 1 → Minimum 2 instances

