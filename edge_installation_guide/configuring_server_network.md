# Configuring Server Network

To configure the networking for the server, run the following commands:

1. Edit the network configuration file by using the following commands:
   
  .. list-table:: Step 1. 
     :widths: 35 65

     * - Commands
       - Remarks
     * - vim/etc/sysconfig/network-scripts/ifcfg-ens32
       - null
     * - DEVICE=ens32
       - null
     * - IPADDR=xxx.xxx.xxx.xxx
       - Use the planned IP address
     * - NETMASK=255.255.255.0
       - null
     * - GATEWAY=yyy.yyy.yyy.yyy
       - Use the planned IP gateway
     * - ONBOOT=yes
       - null
     * - NAME=ens32
       - null
     * - DNS1=zzz.zzz.zzz.zzz
       - Use the planned DNS

2. Start the SSH service by using the following commands:

  .. list-table:: Step 2. Start the ssh service
     :widths: 35 65

     * - Commands
       - Remarks
     * - systemctl restart sshd
       - null
     * - systemctl enable sshd
       - null

You can then acccess and manage the edge server remotely after you complete the above configurations.
