# Site to site

A site-to-site virtual private network (VPN) is a connection between two or more networks, such as a corporate network and a branch office network. Many organizations use site-to-site VPNs to leverage an internet connection for private traffic as an alternative to using private MPLS circuits.

Site-to-site VPNs are frequently used by companies with multiple offices in different geographic locations that need to access and use the corporate network on an ongoing basis. With a site-to-site VPN, a company can securely connect its corporate network with its remote offices to communicate and share resources with them as a single network.

## Create a Site-to-Site

Go to "site-to-site" configuration page

![image](https://user-images.githubusercontent.com/6083644/216993179-a21fec24-98eb-48f7-b12d-d9ebd6d6e08e.png)

Click on "create site"

![image](https://user-images.githubusercontent.com/6083644/216993306-199e7e72-1393-49c0-9916-253746794cb1.png)

Then a window will show up. Define a name for your site.

## Broadcast

This option selects the way broadcast packets are sent to other daemons.  NOTE: all nodes in a VPN must use the same Broadcast mode, otherwise routing loops can form.
If no, broadcast packets are never sent to other nodes.

## Mode

### Router
  
In this mode Subnet variables in the host configuration files will be used to form a routing table.  Only unicast packets of routable protocols (IPv4 and IPv6) are supported in this mode.
                     
### Switch

In this mode the MAC addresses of the packets on the VPN will be used to dynamically create a routing table just like an Ethernet switch does.  Unicast, multicast and broadcast packets of every protocol that runs over Ethernet are supported in this mode at the cost of frequent broadcast ARP requests and routing table updates.

This mode is primarily useful if you want to bridge Ethernet segments. By selecting switch mode, Subnet parameter will be ignored.

## Interface

Select nodes you want in your site. 

![image](https://user-images.githubusercontent.com/6083644/216993593-a28ff946-c231-4e8b-bb5d-b18e3c23735a.png)

After confirmation, nodes will be automaticaly updated. You can see the state of the bridge on a device.
