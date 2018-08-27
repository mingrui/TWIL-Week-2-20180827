# TWIL-Week-2-20180827

# Machine Learning

LightGBM library: Better results than XGBoost  
https://github.com/Microsoft/LightGBM

# Privacy

blackholecloud: WireGuard, Pi-Hole capable device with managed and single user server  
http://blackholecloud.com/copy-of-boudica-buy-a-bhc-annual-subscription/

ELI5: BlackHoleCloud

This applies to the BHC I have, the Singularity. It is the black one.

If you are familiar with running a VPN on your laptop then you are halfway there in this ELI5. The BHC has the VPN client software loaded on it and it shares the VPN and or Tor connection with all of your devices.

The Hardware: A small palm of your hand sized USB powered box with two Ethernet ports and two WiFi radios. The radios are 2.4G and the Ethernet ports are 100 Mb/s. As you can imagine there are a lot of ways to configure it and the user interface makes it easy to switch between several pre-set configurations.

If the Internet source is a WiFi access point then one of the WiFi radios (the external radio) will connect to the AP as a client. The THF will share this connection to you via the Ethernet port, or via the internal WiFi radio (which it will expose as another AP) or both simultaneously. I velcro my BHC to my laptop in this mode. My laptop gets to the BHC via the Ethernet cable and my iPad gets to the BHC via the private SSID .

If the Internet source is your tethered phone, same thing. Just plug your phone cable into the BHC. You can turn the BHC into an access point in this mode.

If the Internet source is an Ethernet cable (like in some hotel rooms) you just plug the cable into the WAN port. You can turn the BHC into an access point in this mode too.

Every permutation of it’s connectivity is possible all through the GUI.

Performance: I have a 150 Mb/s Fios connection. Without the VPN on I can get about 95 Mb/s through the Ethernet ports and about 45 Mb/s through the WiFi to an old Apple access point. With the VPN on I can consistently get over 10 Mb/s. This is the biggest change from their older (white) models. They topped out 4.5 to 7Mb/s

Hardware Firewall: By default it blocks all incoming packets from the outside world. It does not even respond to pings.

Blocking Ads and Malware domains: This is just a click away, it works very well and really speeds up things when tethering over the phone.

VPN: It can connect to the OpenVPN servers directly over UDP or TCP. If you are somewhere that is blocking OpenVPN you can wrap the OpenVPN connection in Stunnel. (https://www.stunnel.org/index.html) It feels only a little slower then a regular TCP connection, but I have not quantified this. I have successfully used this in China where a regular OpenVPN connection would not work.

Tor: There are several ways to connect to Tor.

You can connect to the VPN and then go through the VPN to a Tor entry node.
Each VPN server that is built for you also has a private Tor bridge. The BHC uses Obfsproxy to make the connection. This is a good and stealthy way to get to Tor when local snoopers might be looking for Tor traffic.

Doing the above combinations of connections would be a lot of software to install and time to configure on a laptop, and on a phone or tablet it might not be possible.

The VPN Server(s): There is however a philosophical difference in how the infrastructure is configured. All VPN services I know of share the vpn servers with all the other users. BHC spins up a VPN server (or three) just for you and configures the TinyHardwareFirewall(s) to connect to those servers. These servers can be in your choice of 19 cities in 10 countries. There is zero logging on the servers.

Resource Availability: Having your own server means that you are not competing with any other user for bandwidth or CPU cycles. My experience has been very good and consistent. I can get over 10 Mb/s through the VPN. (I am in North America and my servers are in the U.S. and Western Europe).

Anonymity: With shared VPNs there is a sense of anonymity since you are in a crowd of traffic. If your adversary is a state actor then this level of anonymity is trivial to pierce. Anonymity is hard. If you are a criminal this is probably not a good choice.

Security: On a shared VPN server you may be at risk if other users computer’s are be infected with viruses or if other users users are actively trying to hack the VPN server or other VPN users. How much risk there is depends on the configuration of the server and the existence of zero days for the vpn server’s software stack.
