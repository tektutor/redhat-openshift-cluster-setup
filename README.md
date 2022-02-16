# RedHat OpenShift Production Grade Setup with KVM installed on CentOS 7.9 64-bit
As RedHat CentOS 8.x has reached its End of Life by 31st Dec 2021 and official software updates were stopped from 31st Jan 2022, I decided to use RedHat CentOS 7.9 64-bit as this will reach its End of Life only by 30th June, 2024.

You may as well consider substituting CentOS 7.9 64-bit with Fedora 35 or Rocky Linux 8.x or RedHat CentOS Stream or Oracle Enterprise Linux or RedHat Enterprise Linux 8.x as per your preference. But make sure it is one of the Enterprise Linux distribution of your choice.

We are going to setup a Production Grade RedHat OpenShift Container Platform v4.9 which used Kubernetes v1.22.

I'll be installing dnsmasq as the DNS Server on CentOS 7.9 64-bit and KVM as the Hypervisor.  All the nodes listed in the cluster
will be created as KVM virtual machines running on CentOS v7.9 on the same Physical Server. However, in actual production environment it is recommended to spread the master and worker nodes onto different Physical Servers for High Availability(HA).

Once we are done with the setup, the RedHat OpenShift Cluster will have 
<pre>
master-1        64 GB RAM, 8 Cores and 500 GB HDD
master-2        64 GB RAM, 8 Cores and 500 GB HDD
master-3        64 GB RAM, 8 Cores and 500 GB HDD
worker-1        64 GB RAM, 8 Cores and 500 GB HDD
worker-2        64 GB RAM, 8 Cores and 500 GB HDD

LoadBalancer    16 GB RAM, 2 Cores and 100 GB HDD
BootStrap Node  16 GB RAM, 4 Cores and 300 GB HDD  - This node will be deleted once the setup is ready
</pre>
### System Configuration that I used
<pre>
PowerEdge R630 
Processor Type: Intel(R) Xeon(R) CPU E5-2683 v4 @ 2.10Ghz
  - Logical Processors: 64
NICs : 4
512 GB RAM
6 TB HDD
</pre>
