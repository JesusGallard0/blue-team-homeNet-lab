#Network segmentation attempt(Home LAN)

##Objective 
-Attempt to implement network segmentation within a home LAN environment in order to separate devices based on risk level and functionality

#Environment 
-ISP-provided router(default firmware)
-Multiple SSIDs available(2.4GHz/5GHz)
-Router web configuration panel

#Approach
-The initial approach was to use multiple SSIDs to create separate network segments,for example
-Main network
-Lab network
-Guest/restricted network

#Router configuration
-The router was able to create an cofigure multiple SSIDs
-Basic settings per SSID:
    -Name
    -Encryption Type
    -Password
    -MAC filtering

*However,no support was found for:
-VLAN configuration
-Separate IP subnets per SSID
-Firewall rules between networks
-Interface or bridge separation

#Findigs
1.All SSIDs are bridged into the same LAN network so devices connected to different SSIDs still share the same IP subnet and can communicate freely
2.The SSIDs provide organizational separation but not actual network isolation
3.MAC filtering allowed but it does not prevent communication between devices on the LAN 
4.Can be bypassed via MAC spoofing

#Conclusion
-The router does not support true network segmentation,the available features do not provide isolation between devices or reduce lateral movement within the network

##Effective network segmentation requires
-VLAN support
-Separate subnets
-Firewall rules between network zones










