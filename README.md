# Downloading and Configuring VyOS in VMware
VyOS is an open-source network operating system based on Debian. It provides a free routing platform that competes directly with other commercially available solutions from well-known network providers. VyOS is run on standard amd64 systems, making it able to be used as a router and firewall platform for cloud deployments. VyOS is fully open-source and community-driven, which is its distinctive advantage. It uses a monolithic kernel type and is available in English. VyOS is an enterprise-grade router platform that focuses on enterprise, service provider, and network geek audiences. It includes features such as VRRP for IPv4 and IPv6, ECMP, stateful load balancing, and built-in versioning. 

VyOS also has a convenient VMware download. Head to https://vyos.io/ and click the VyOS on VMware link to get the latest release.

Once the download is complete open the .ova file to import it into VMware. Open the settings dialog for the VM so we can configure the network interfaces. Since this is a router/firewall it ships with two interface. Configure one to connect to the 10.10.10.0/24 Host-only network and one to connect to the 192.168.148.0/24 NAT network. 

Your settings should be similar to the ones below.

![VyOS1](https://github.com/malvika-thakur/VyOS/assets/60217652/3789f957-13fe-4c47-acfe-256dab25725d)

Start the VM and sign in with the credentials ```vyos```:```vyos```

The next step is to assign addresses and descriptions to the interfaces in VyOS.

![vyos2](https://github.com/malvika-thakur/VyOS/assets/60217652/37799953-15be-489a-abc0-57d9ab9b0c8b)

Run the command below to verify your settings.

![vyos3](https://github.com/malvika-thakur/VyOS/assets/60217652/bfcd5d11-755a-4820-bf22-5f1e7be3b004)


We now need to set some firewall rules. We won’t go into all the ins and outs of creating a firewall in VyOS but the basic process is you create IN, OUT, and LOCAL policies that are composed of rules and then you apply the policies to an interface. The following commands will lock down 10.10.10.0/24 to only allow inbound port 8585 and outbound connections over port 443.

First set a default action to drop anything that does not match a rule.

![vyos4](https://github.com/malvika-thakur/VyOS/assets/60217652/829562c9-9a0c-45b7-a213-87b68bbf9b03)


Allow inbound connections that are established and related.

![vyos5](https://github.com/malvika-thakur/VyOS/assets/60217652/ea84677e-e4da-44de-86fe-40b1e49b9a0a)


Open port 8585 so we can access the metasploitable3 web app.

![vyos6](https://github.com/malvika-thakur/VyOS/assets/60217652/0001f7b6-e574-4c9c-b9c6-82793161690b)


Now for the outbound rules. Allow established or related traffic.

![vyos7](https://github.com/malvika-thakur/VyOS/assets/60217652/eb63f69d-fb95-4f14-b2ae-06e481a6730f)


We are only allowing outbound on 443(https). That’s secure, right?

![vyos8](https://github.com/malvika-thakur/VyOS/assets/60217652/403c81a6-38ab-4e06-865f-7b43c373a51f)


Commit, save, and reboot.

![vyos9](https://github.com/malvika-thakur/VyOS/assets/60217652/f32bb8b4-68a3-4756-822d-66bf77f436ed)
