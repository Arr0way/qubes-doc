---
layout: wiki
title: VPN
permalink: /wiki/VPN/
---

VPN connections in Qubes
------------------------

The simplest case if you set up a VPN connection using the Network Manager inside one of your VMs. Setting up such a connection is really not Qubes specific and it is documented in Your Operating system documentation.

If you using the Qubes default OS (Fedora): [​Establishing a VPN Connection](http://docs.fedoraproject.org/en-US/Fedora/18/html/System_Administrators_Guide/sec-Establishing_a_VPN_Connection.html)

The Qubes specific part is choose the right VM for the VPN client:

### NetVM

The simplest case if you set up a VPN connection using the Network Manager inside your NetVM. Because the [NetworkManager?](/wiki/NetworkManager) already started you are ready to set up your VPN connection. However this has some disadvantages:

-   You have to place (and probably save) Your VPN credentials inside the NetVM wich is directly connected to the outside world
-   All your AppVMs wich are connected to the NetVM will be connected to the VPN (by default)

### ProxyVM

One of the best thing in Qubes that you can use a specian type of VMs called ProxyVM (or FirewallVM). The special thing is that your AppVMs see this as a NetVM, and the NetVMs see it as an AppVM. Because of that You can place a ProxyVM between your AppVMs and Your NetVM. This is how the default firewall VM is working.

Using a ProxyVM to set up a VPN clinet will gives you the ability to:

-   Separate your VPN credentials from Your AppVM data.
-   You can easily controll wich of your AppVMs are connected to your VPN by simply set it as a NetVM of the desired AppVM.

To setup a ProxyVM as a VPN gateway you should:

-   create a new VM and check the ProxyVM radiobutton
-   add the network-manager service to this new VM
-   strart the new ProxyVM and set up Your VPN as described in the Network Manager documentation linked above.
-   connect your AppVMs to use the VPN service.

### AppVM

While the Network Manager is not started here (for a good reason) You can configure any kind of VPN client in your AppVM as well, however it is only suggested if you have to use a special VPN clinet.