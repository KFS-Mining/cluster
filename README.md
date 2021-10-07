# Long Term Network Plan

The networks shall be accessable through a single VPN. Within that VPN, there shall eb three networks:

1. Kubernetes - there shall be a kubernetes cluster, consisting of controllers and workers
2. ESXi / Proxmox - there shall be a cluster used to manage and deploy VMs, using a service similar to ESXi or Proxmox
3. Workload Manager - there shall be a cluster with a workload manager like SLURM, consisting of high quality CPUs and GPUs

## Machines

* `192.168.0.5`: kubernetes controller
	* 30001: kubernetes dashboard
	* 21: SSH Dropbear server 
* `192.168.0.10`: pi worker
	* 21: SSH Dropbear server 
* `192.168.0.11`: pi worker
	* 21: SSH Dropbear server 
* `192.168.0.12`: pi worker
	* 21: SSH Dropbear server 

## Necesarry Services

### Kubernetes Deployments

The following services shall be managed through Kubernetes:

1. Kubernetes dashboard
2. Hardware managment and monitoring
3. DNS server
4. KFS Dashboard
5. A log collection server

### Kubernetes Nodes

All nodes in kubernetes -- workers and controllers -- shall run the following services:

* SSH / 21 (Dropbear)

## IPs
192.168.0.3-7: controll nodes
192.168.0.10-50: worker nodes
192.168.0.200-249: DHCP