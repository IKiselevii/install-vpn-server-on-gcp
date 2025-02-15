# Install VPN Server on Google Cloud platform (using Debian 9)

----

Thanks a lot to [Eliot](https://github.com/elliot79313) 
for his [instructions](https://github.com/elliot79313/install-vpn-server-on-gcp), but it's written for debian 7, which is outdated now. Instructions are very helpful 
during installing VPN on GCP server with Debian 9 stretch basic image. 

Instructions updated and now you're able to run VPN on GCP without any difficulties.

-----

###Prerequisite:
1. You have Google account
2. You are familiar with [Google cloud platform console](https://console.developers.google.com "Google Cloud Platform Console").
3. You know how to launch Google Computing VM with Debian 9. ([Quick Start](https://cloud.google.com/compute/docs/linux-quickstart "Quick Start"))


-----

##Instructions:


###On Server:

1. Install strongswan, you have do it manually - <code>apt-get install strongswan</code>
2. After you launch an instance, download <code>vpn-installtion.sh</code> into that instance.
3. Update the **TODO** (<code>IPSEC_PSK</code>, <code>VPN_USER</code>, <code>VPN_PASSWORD</code>, <code>PRIVATE_IP</code>, <code>PUBLIC_IP</code>)
4. run <code>
	sudo sh vpn-installtion.sh
</code>
4. Setup the network.
![Allow traffic to TCP port 500, and UDP ports 500 and 4500.](https://greenido.files.wordpress.com/2014/08/screenshot-2014-08-10-08-50-20.png?w=696)

-----

###On Client(Mac):
1. Create a new connection. ![Create a new connection](https://raw.github.com/elliot79313/install-vpn-server-on-gcp/master/img/client_networksetup.png)
2. Fill in the Server Address and Account Name.
3. Click Authentication Settings. Fill in Machine Authentication Shared Secret with **IPSEC_PSK**
4. Click advanced button and check **Send all traffic** on options tab.
5. Click apply and connect.
6. [Optional] Setup dns server. In DNS tab, you can copy values in <code>/etc/resolv.conf</code> of VPN Server and update the **search domain** of client.


###On Client(Keenetic OS):
1. On keenetic folder Internet - Other connections - Create connection
2. Fill fields in a menu with EXTERNAL_IP and VPN user's credentials. Use L2TP protocol to connection.
Set flag on **Use for accessing the Internet**! ![Keenetic OS menu](https://raw.github.com/IKiselevii/install-vpn-server-on-gcp/master/img/keenetic_network_setup.png)

-----

Feel free to open issues.
