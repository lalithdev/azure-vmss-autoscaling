# Azure VMSS Autoscale

## Project Overview

This project demonstrates the deployment and configuration of an **Azure Virtual Machine Scale Set (VMSS)** with **CPU-based autoscaling**.

The VM Scale Set maintains a minimum number of instances and automatically adds or removes instances based on average CPU utilization.

## Architecture

The project follows this architecture:

```text
                    Azure Resource Group
                    VMSS-Autoscale-RG
                            |
                            v
                +-----------------------+
                | Azure VM Scale Set    |
                | vmss-autoscale-demo   |
                +-----------+-----------+
                            |
                  +---------+---------+
                  |                   |
                  v                   v
             VM Instance 1       VM Instance 2
             Ubuntu 24.04        Ubuntu 24.04
                  |                   |
                  +---------+---------+
                            |
                            v
                     Azure Monitor
                            |
                     Percentage CPU
                            |
                            v
                    Azure Autoscale
                     /          \
                    /            \
             CPU > 70%          CPU < 30%
                 |                  |
                 v                  v
             Scale Out           Scale In
                +1                  -1
                 |                  |
                 v                  v
          Maximum 5            Minimum 2
```

For more details, see [Architecture](architecture.md).

## Azure Services Used

| Service                          | Purpose                             |
| -------------------------------- | ----------------------------------- |
| Azure Virtual Machine Scale Sets | Manage multiple VM instances        |
| Azure Virtual Machines           | Run the Ubuntu VM instances         |
| Azure Virtual Network            | Provide network connectivity        |
| Network Security Group           | Control inbound network traffic     |
| Azure Monitor                    | Monitor CPU utilization             |
| Azure Autoscale                  | Automatically change instance count |
| Azure Resource Group             | Organize Azure resources            |

See [Azure Services](services.md).

## VMSS Configuration

The project uses:

| Setting             | Value                 |
| ------------------- | --------------------- |
| VMSS Name           | `vmss-autoscale-demo` |
| Operating System    | Ubuntu 24.04          |
| VM Size             | Standard_B2s_v2       |
| Minimum Instances   | 2                     |
| Default Instances   | 2                     |
| Maximum Instances   | 5                     |
| Scale Out Threshold | CPU > 70%             |
| Scale Out Action    | Increase by 1         |
| Scale In Threshold  | CPU < 30%             |
| Scale In Action     | Decrease by 1         |

## Deployment

The VM Scale Set was deployed in the Azure Portal under the resource group:

```text
VMSS-Autoscale-RG
```

Deployment details are available in [Deployment](deployment.md).

## Autoscaling

The autoscale configuration uses **Average Percentage CPU** as the scaling metric.

### Scale Out

```text
Average CPU > 70%
        ↓
Increase instance count by 1
```

### Scale In

```text
Average CPU < 30%
        ↓
Decrease instance count by 1
```

The instance count is maintained between **2 and 5 instances**.

See [Autoscaling](autoscaling.md).

## Monitoring

Azure Monitor was used to observe the **Percentage CPU** metric of the VM Scale Set.

The CPU metric was used to verify the conditions used by the autoscale configuration.

See [Monitoring](monitoring.md).

## CPU Load Testing

CPU load was generated on the Ubuntu VM using the `stress` utility.

```bash
sudo apt update
sudo apt install -y stress
stress --cpu 2 --timeout 600
```

The generated CPU load was monitored through Azure Monitor.

See [Testing](testing.md).

## Screenshots

### 1. Resource Group

![Resource Group](screenshots/01-resource-group.png)

### 2. VMSS Validation

![VMSS Validation](screenshots/02-vmss-validation.png)

### 3. VMSS Deployment

![VMSS Deployment](screenshots/03-vmss-deployment.png)

### 4. Initial VMSS Instances

![Initial Instances](screenshots/04-initial-instances.png)

### 5. Autoscale Limits

![Autoscale Limits](screenshots/05-autoscale-limits.png)

### 6. Autoscale Rules

![Autoscale Rules](screenshots/06-vmss-autoscale-rules.png.png)

### 7. VMSS Metrics

![VMSS Metrics](screenshots/07-vmss-metrics.png.png)

### 8. CPU Metrics

![CPU Metrics](screenshots/08-vmss-cpu-metrics.png.png)

### 9. VMSS Instances

![VMSS Instances](screenshots/09-vmss-instances.png)

### 10. SSH Inbound Rule

![SSH Inbound Rule](screenshots/10-ssh-inbound-rule.png.png)

### 11. CPU Load Test

![CPU Load Test](screenshots/11-cpu-load-test.png.png)

### 12. Final Autoscale Configuration

![Final Autoscale Configuration](screenshots/12-autoscale-final.png.png)

## Project Documentation

* [Architecture](architecture.md)
* [Azure Services](services.md)
* [Deployment](deployment.md)
* [Autoscaling](autoscaling.md)
* [Monitoring](monitoring.md)
* [Testing](testing.md)
* [Commands](commands.md)
* [Result](result.md)

## Result

The Azure Virtual Machine Scale Set was configured with CPU-based autoscaling.

The project demonstrates monitoring VMSS CPU utilization through Azure Monitor and configuring autoscale rules to increase or decrease the number of VM instances according to CPU thresholds.

## Conclusion

This project demonstrates the use of Azure VM Scale Sets, Azure Monitor, and Azure Autoscale to manage VM instances dynamically based on CPU utilization.
