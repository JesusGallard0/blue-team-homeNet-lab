#UPnP hardening

##Objective 
-Reduction of attack surface by disabling automatic NAT port exposure(UPnP) and replaciing it with explicit,audited port forwarding when required


##UPnP
-UPnP (Universal Plug and Play) allows devices in the LA to request automatic port forwarding,it works via SSDP(UDP1900) and affects NAT behavior on the router


##Risk Analysis
*WHY disable it
-Devices can expose services without user awareness
-Malware can open ports silently
-Expands external attack surface
-Lacks strong authentication in many implementations

##Action Taken
-I decided to disable the UPnP service in the Router Settigs
-Verified change by upnpc -l ,theres an UPnP service but is from the TV Box,some devices still advertise themselves via UPnP (rootdevice) but at least there is not valid UPnP Internet Gateway Device (IGD), confirming that the router no longer exposes automatic port mapping services. This mitigates the risk of internal devices opening ports to the WAN without authorization. Other UPnP devices (e.g., media boxes, IoT devices) remain present but are contained within the LAN.

##Impact 
*Unaffected services:
-Web browsing
-Streaming
-Calls and messaging apps
-Online games(client-server)
*Potential limitations:
-Strict NAT type in some games
-Hosting servers may require manual configuration
-Peer-to-peer connectivity less efficient

*Just when needed:
-Hosting a game server
-Running a local service exposed to internet
1.Identify required ports
2.Assign static IP to host
3.Create manual port forward in the router settings
4.Verify exposure

*Security Practices
-Only open required ports
-Close them when not in use
-Prefer:
    -Whitelisting IPs(if supported)
    -Non-default ports
-Never expose:
    -SSH(22)
    -RDP(3389)
    -SMB(445)


"Next improvements:Network segmentation"

