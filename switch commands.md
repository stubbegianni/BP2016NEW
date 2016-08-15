# all switches

en
conf t
enable secret class
no ip domain-lookup
line console 0
password cisco
login
line vty 0 15
password cisco
login
end
copy running-config startup-config

# Switch 1
conf t
vtp mode server
vtp domain Lab5
vtp password cisco
exit
int fa0/1
switchport mode trunk
switchport trunk native vlan 99
no shut
exit
vlan 99
name management
vlan 10
name faculty-staff
vlan 20
name students
vlan 30
name guest
exit
int vlan99
ip address 172.17.99.11 255.255.255.0
exit
spanning-tree vlan 99 priority 4096
exit

# Switch 2

interface fa0/6
switchport mode access
no shutdown
interface fa0/11
switchport mode access
no shutdown
interface fa0/18
switchport mode access
no shutdown
end
vtp mode client
vtp domain Lab5
vtp password cisco
end
int fa0/1
switchport mode trunk
switchport trunk native vlan 99
no shut
int vlan99
ip address 172.17.99.12 255.255.255.0
int fa0/6
switchport access vlan 30
int fa0/11
switchport access vlan 10
int fa0/18
switchport access vlan 20
end
copy running-config startup-config