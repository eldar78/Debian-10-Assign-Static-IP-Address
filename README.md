# Debian-10-Assign-Static-IP-Address
Assign Static IP Address on Debian 10

Edit the network configuration file by running the following command.
    sudo cp /etc/network/interfaces /etc/network/interfaces.backup 
    sudo nano /etc/network/interfaces

This file may look like the following.

Edit the configuration as follows.

    auto ens18
    iface ens18 inet static
      address 192.168.0.2
      netmask 255.255.255.0
      gateway 192.168.0.1
      dns-nameservers 89.207.128.252 89.207.130.252

Or like this, as I have in my config file on VMWARE 
-------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
#iface ens32 inet dhcp # Change it to your network interface name as I did
auto eth0
iface eth0 inet static
           address 192.168.233.167
           netmask 255.255.255.0
           dns-nameservers 8.8.8.8 8.8.4.4
           gateway 192.168.233.2


-------------------------------------



Make sure not to change the loopback adapter config. After the change, it will look something like the following screenshot.

Save the file and exit from the editor.
Step 5: Restart Networking Service

Restart the networking service so that the updated configuration can be applied. Run the command.

    sudo systemctl restart networking

Conclusion

In this tutorial, we have learned how to configure a static IP address on Debian 10 “Buster” server. Your server is now configured to use static IP address.
