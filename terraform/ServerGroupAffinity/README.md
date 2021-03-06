# Affinity Server Group

The following resources will be created by the template:

* A new network
* Two subnets within the network
  * The first subnet is an IPv4 subnet with a hardcoded cidr: 10.0.8.0/24
  * The second subnet is an IPv6 subnet, dynamically generated from an existing subnet pool
  * The name or ID of the subnet pool can be updated in the vars.tf file
* A router with the new subnets assigned and internet connection
* A new security group with the following rules:
  * Ingress ICMP for IPv4 and IPv6 from any destination
  * Ingress SSH for IPv4 and IPv6 from any destination
* Two server groups with affinity policy set
  * One group for each AZ
  * VMs within the same server group are spawned on the same hypervisor
* Four VMs - Two in each server group
  * The field `hostId` has the same value for all servers within a server group
