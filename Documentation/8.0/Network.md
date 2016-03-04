#Arctic LAN 8.0 Network Configuration Notes
*Mostly written by Chris Bailey in 2015. Not actually posted anywhere until 2016.*

##Overview
We talked to IT and was given a router which was configured with minimal filtering. This router sat between the CTHS network and our ArcticLAN network, and handled DHCP. DNS was handled by CTHS's domain controller. Because of that, all we had to set up were the switches, as opposed to previous years where we had to run our own routers, DNS, and DHCP as well. 

##Network Diagram
###Legend
* Other networks: `{_name_}`
* Routers: `(_name_)`
* Switches: `[name]`
* PC/console/etc: `@`
* Network cable: `|`
* Patch panel: `[#######]`
* Floor drop: `#`
* Table: `==devices==`

###Logical
               __________________
              {_Rest_of_internet_}
                      |
                  ____|_____
                 {_MSBSD_WAN_}
                      |
                  ____|_____
                 {_CTHS_LAN_}
                      |
                 _____|_______
                (_IT-provided_)
                      |
              ________|__________
             [_______Core________]
            /    |         |      \
           /     |         |       \
    [Access0] [Access1] [Access2] [Access3] ... etc.
     | | | |   | | | |   | | | |   | | | |
     @ @ @ @   @ @ @ @   @ @ @ @   @ @ @ @ ... etc.
     
###Physical
IDF:

     _______________________
    [_CTHS_access_Enterasys_]
               |
         ______|______
        (_IT-provided_)
               |
            ___|__
           [_Core_]
            ||||||
           [######]

Commons:

     ==@@[A0]@@==    ==@@[A1]@@== 
           |              |
           #              #
           |              |
     ==@@[A2]@@==    ==@@[A3]@@== 

     ==@@[A4]@@==    ==@@[A5]@@== 
           |              |
           #              #
           |              |
     ==@@[A6]@@==    ==@@[A7]@@== 

     ==@@[A8]@@==    ==@@[A9]@@== 
           |              |
           #              #
           |              |
     ==@@[A10]@@==   ==@@[A11]@@== 

##Switch configuration
I don't have the complete config files lying around anywhere, but here are the most important settings.
###Core
* Ports 0-23: Default config, NO portfast.

###Access
* Port 0: Default config, NO portfast. Connects to floor drops.
* Port 1-23: Default config, but enable portfast. Connects to PCs and consoles.

##Conclusion
Hopefully these are helpful to future organizers. If you have questions, [let me know](http://chrisbailey.io/contact) and I'll tell you anything else I remember.
