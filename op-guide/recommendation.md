---
title: Software and Hardware Requirements
category: operations
---

# Software and Hardware Requirements

## About

As an open source distributed NewSQL database with high performance, TiDB can be deployed in the Intel architecture server and major virtualization environments and runs well. TiDB supports most of the major hardware networks and Linux operating systems. 

## Linux OS Version Requirements

| Linux OS Platform        | Version      |
| :-----------------------:| :----------: |
| Red Hat Enterprise Linux | 7.3 and above|
| CentOS                   | 7.3 and above|
| Oracle Enterprise Linux  | 7.3 and above|
| Ubuntu LTS               | 14.04 and above|

**Note**

- For Oracle Enterprise Linux, TiDB supports the Red Hat Compatible Kernel (RHCK) and does not support the Unbreakable Enterprise Kernel provided by Oracle Enterprise Linux.
- The support for the Linux operating systems above include the deployment and operation in physical servers as well as in major virtualized environments like VMware, KVM and XEM.

## Server Requirements

You can deploy and run TiDB on the 64-bit generic hardware server platform in the Intel x86-64 architecture. The requirements and recommendations about server hardware configuration for development, testing and production environments are as follows:

### Development and Testing Environments

| Component | CPU     | Memory | Local Storage  | Network  | Instance Number (Minimum Requirement) |
| :------: | :-----: | :-----: | :----------: | :------: | :----------------: |
| TiDB    | 16 core+   | 16 GB+  | SAS, 200 GB+ | Gigabit network card | 1       |
| PD      | 16 core+   | 16 GB+  | SAS, 200 GB+ | Gigabit network card | -       |
| TiKV    | 16 core+   | 32 GB+  | SAS, 200 GB+ | Gigabit network card | 3       |
|         |         |         |              | Total Server Number |  4      |     

**Note**

- In the test environment, the TiDB and PD can be deployed on the same server.
- For performance-related testing, do not use low-performance storage and network hardware configuration, in order to guarantee the correctness of the test result.

### Production Environment

| Component | CPU | Memory | Hard Disk Type | Hard Disk Number | Single Hard Disk Size | Network | Instance Number (Minimum Requirement) |
| :-----: | :------: | :------: | :------: | :------: | ------ | :------: | :-----: |
|  TiDB  | 32 core+ | 128 GB+ | SSD | 2+ | 500 GB+ | 2 or more 10 Gigabit network cards | 2 |
| PD | 16 core+ | 32 GB+ | SSD | 2+ | 200 GB+ | 2 or more 10 Gigabit network cards | 3 |
| TiKV | 32 core+ | 128 GB+ | SSD | 2+ | 200~500 GB. | 2 or more 10 Gigabit network cards | 3 | 
| Monitor | 16 core+ | 32 GB+ | SAS | 4+ | 200 GB+ | 2 or more Gigabit network cards | 1 |
|     |     |     |      |      |      |  Total Server Number   |    9   |

**Note**:   

- In the production environment, you can deploy and run TiDB and PD on the same server. If you have a higher requirement for performance and reliability, try to deploy them separately.
- It is strongly recommended to use higher configuration in the production environment.
- It is recommended to keep the size of TiKV hard disk within 500G in case it takes too long to restore data when the hard disk is damaged.

## Network Requirements

As an open source distributed NewSQL database, TiDB requires the following network port configuration to run. Based on the TiDB deployment in actual environments, the administrator can enable relevant ports in the network side and host side. 

| Component | Default Port | Description |
| :--:| :--: | :-- |
| TiDB |  4000  | the communication port for the application and DBA tools|
| TiDB | 10080  | the communication port to report TiDB status|
| TiKV |  20160 | the TiKV communication port  |
| PD | 2379 | the communication port between TiDB and PD |
| PD | 2380 | the inter-node communication port within the PD cluster |
| Prometheus |  9090| the communication port for the Prometheus service|
| Pushgateway |  9091| the aggregation and report port for TiDB, TiKV, and PD monitor |
| Node_exporter |  9100| the communication port to report the system information of every TiDB cluster node |
| Grafana | 3000 | the port for the external Web monitoring service and client (Browser) access|

## Web Browser Requirements

Based on the Prometheus and Grafana platform, TiDB provides a visual data monitoring solution to monitor the TiDB cluster status. To visit the Grafana monitor interface, it is recommended to use a higher version of Microsoft IE, Google Chrome or Mozilla Firefox.
