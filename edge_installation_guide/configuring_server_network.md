# Configuring Server Network

To configure the networking for the server, run the following commands:

*Table: Step 1. Edit the network configuration file*

<table>
  <tr>
    <td>Commands</td>
    <td>Remarks</td>
  </tr>
  <tr>
    <td>vim/etc/sysconfig/network-scripts/ifcfg-ens32</td>
    <td></td>
  </tr>
  <tr>
    <td>DEVICE=ens32</td>
    <td></td>
  </tr>
  <tr>
    <td>IPADDR=xxx.xxx.xxx.xxx</td>
    <td>Use the planned IP address</td>
  </tr>
  <tr>
    <td>NETMASK=255.255.255.0</td>
    <td></td>
  </tr>
  <tr>
    <td>GATEWAY=yyy.yyy.yyy.yyy</td>
    <td>Use the planned IP gateway</td>
  </tr>
  <tr>
    <td>ONBOOT=yes</td>
    <td></td>
  </tr>
  <tr>
    <td>NAME=ens32</td>
    <td></td>
  </tr>
  <tr>
    <td>DNS1=zzz.zzz.zzz.zzz</td>
    <td>Use the planned DNS</td>
  </tr>
</table>

*Table: Step 2. Start the ssh service*

<table>
  <tr>
    <td>Commands</td>
    <td>Remarks</td>
  </tr>
  <tr>
    <td>systemctl restart sshd</td>
    <td></td>
  </tr>
  <tr>
    <td>systemctl enable sshd</td>
    <td></td>
  </tr>
</table>

You can then acccess and manage the edge server remotely after you complete the above configurations.
