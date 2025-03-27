Related:[[Network Access]]

configure terminal
  enters global configuration mode from privileged EXEC mode

enable
  enters privileged EXEC mode

end
  ends and exits configuration mode

exit
  exits one level in the menu structure

interface type number
  enters interface configuration mode

interface range type [module/][slot/]starting-port - ending-port
  enters interface configuration mode for a range of interfaces

ip address ip-address subnet-mask
  assigns an Internet Protocol (IP) address and subnet mask to an interface

name vlan-name
  configures a name for a VLAN

ping ip-address
  sends an Internet Control Message Protocol (ICMP) Echo Request to the specified address

show interfaces [type number]
  displays interface statistics

show interfaces status
  displays the line status of all interfaces

show vlan brief
  displays parameters for all VLANs; contains the VLAN name, status, and ports assigned to it

shutdown; no shutdown
  disables an interface; enables an interface

switchport access vlan vlan-id
  assigns an access port to a VLAN

switchport mode access
  configures an interface as an access port

vlan number [name vlan-name]
  creates or configures a VLAN with an optional name