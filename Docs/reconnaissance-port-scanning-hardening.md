Scanning and Securing my Local Network.Part1

#Objective
Identify active devides and exposed services in my local network,analize potential risks,and reduce unnecessary attack surface

1.Host Discovery & Inital Scan
First,I identified my IP address using ip a
then i scanned my local network nmap ip/24
this allowed me to enumerate active devices on the LAN

2.Analysis
##MY MAIN PC
i deteceted an open port 
*Port5357(WS-Discovery)

*_Looked for it in google ,its a port used by Windows for device discovery(printers and scanners)
*_Its typically limited to local network communication
*_Its not critical if its restricted to LAN but it could be leveraged for lateral movement if an attacker gains access

I decided to stop that port so i looked into win10 control panel>Network and Sharing Center>Advanced Sharing settings

once i stoped it i re scanned in my Kali VM and everything was normal now,its worth noting that this time im doing a simple scann ,just the 1000 main ports ,nothing deeper,that comes later

##MY VM KALI LINUX

I discovered another device eposing
*Port80(HTTP)
i used ss -tulnp
apache2 was running by default at startup

i decided to stop and disable apache2 but then something unexpected happened,my nmap ip/24 wasnt working,but just talking about my VM IP, when it had to scann my own VM IP it just frezzed ,i tried to reboot,maybe up to date the whole VM,but then i realized that my VM cant scan my own IP anymore if theres not an open port ,when i open a port it just works again as usual

Looking for the problem ,which one was hard to find and im not even sure about it,maybe its related to Nmap host discovery behavior,but well...this lab is not for this but i couldnt find how to fix it,at least the port was closed

##Router Analysis

Detected open/filtered ports
*22(SSH)
*23(telnet)
*53(DNS)
*80/443(web interface)
*52869(unknown)

*_SSH and Telnet are potentially critical if exposed exernally 
*_DNS (53) is expected
*_80/443 used for router management in a web site

This time i decided that i just can change the WIFI password and Router admin credentials
And i decided to make a second lab improving it by getting into UPnP,check for remote management and ,maybe setting a Guest WIFI

##TV Box device
Detected ports
*_8008/8009 (control services)
*_8443(secure web interface)
*_9000(internal service)

Risk onlyincreases if an attacker gains LAN acces

The thing that i can try to do is moving the device to a Guest Network by network segmentation but ill do it in the part2

#This time i learned about some usual ports used by routers and how to keep a basic safe Local Network evironment







