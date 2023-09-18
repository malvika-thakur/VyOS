# Downloading and Configuring VyOS in VMware
VyOS is an open-source network operating system based on Debian. It provides a free routing platform that competes directly with other commercially available solutions from well-known network providers. VyOS is run on standard amd64 systems, making it able to be used as a router and firewall platform for cloud deployments. VyOS is fully open-source and community-driven, which is its distinctive advantage. It uses a monolithic kernel type and is available in English. VyOS is an enterprise-grade router platform that focuses on enterprise, service provider, and network geek audiences. It includes features such as VRRP for IPv4 and IPv6, ECMP, stateful load balancing, and built-in versioning. 

VyOS also has a convenient VMware download. Head to https://vyos.io/ and click the VyOS on VMware link to get the latest release.

Once the download is complete open the .ova file to import it into VMware. Open the settings dialog for the VM so we can configure the network interfaces. Since this is a router/firewall it ships with two interface. Configure one to connect to the 10.10.10.0/24 Host-only network and one to connect to the 192.168.148.0/24 NAT network. 

Your settings should be similar to the ones below.

![VyOS1](https://github.com/malvika-thakur/VyOS/assets/60217652/3789f957-13fe-4c47-acfe-256dab25725d)

Start the VM and sign in with the credentials vyos:vyos

The next step is to assign addresses and descriptions to the interfaces in VyOS.

Run the command below to verify your settings.
