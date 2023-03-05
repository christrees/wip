
## Current winfield
```
[admin@ngMikrotik] > export
# mar/04/2023 15:28:57 by RouterOS 7.8
# software id = G96Q-AWXF
#
# model = RB951G-2HnD
# serial number = 3E2E02AA4090
/interface bridge
add admin-mac=D4:CA:6D:7C:E6:53 auto-mac=no fast-forward=no mtu=1500 name=bridge-local
/interface ethernet
set [ find default-name=ether1 ] name=ether1-gateway speed=100Mbps
set [ find default-name=ether2 ] name=ether2-master-local speed=100Mbps
set [ find default-name=ether3 ] name=ether3-slave-local speed=100Mbps
set [ find default-name=ether4 ] name=ether4-slave-local speed=100Mbps
set [ find default-name=ether5 ] name=ether5-slave-local speed=100Mbps
/interface wireless
set [ find default-name=wlan1 ] antenna-gain=0 band=2ghz-b/g/n channel-width=20/40mhz-Ce country=no_country_set distance=indoors \
    frequency-mode=manual-txpower mode=ap-bridge ssid=MikroTik station-roaming=enabled wireless-protocol=802.11
/interface list
add exclude=dynamic name=discover
add name=WAN
add name=LAN
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/ip ipsec proposal
set [ find default=yes ] enc-algorithms=3des
/ip pool
add name=dhcp ranges=192.168.2.170-192.168.2.199
/ip dhcp-server
add address-pool=dhcp authoritative=after-2sec-delay interface=bridge-local lease-time=3d name=default
/system logging action
set 0 memory-lines=100
set 1 disk-lines-per-file=100
/interface bridge port
add bridge=bridge-local interface=ether2-master-local
add bridge=bridge-local interface=wlan1
add bridge=bridge-local interface=ether3-slave-local
add bridge=bridge-local interface=ether4-slave-local
add bridge=bridge-local interface=ether5-slave-local
/ip neighbor discovery-settings
set discover-interface-list=discover
/interface list member
add interface=ether1-gateway list=discover
add interface=ether2-master-local list=discover
add interface=ether3-slave-local list=discover
add interface=ether4-slave-local list=discover
add interface=ether5-slave-local list=discover
add interface=bridge-local list=discover
add interface=ether1-gateway list=WAN
add interface=bridge-local list=LAN
/interface ovpn-server server
set auth=sha1,md5
/ip address
add address=192.168.2.1/24 comment="default configuration" interface=bridge-local network=192.168.2.0
/ip dhcp-client
add comment="default configuration" interface=ether1-gateway
/ip dhcp-server lease
add address=192.168.2.195 client-id=1:ce:cb:42:90:9f:ab mac-address=CE:CB:42:90:9F:AB server=default
add address=192.168.2.200 mac-address=CE:CB:42:90:9F:AB
/ip dhcp-server network
add address=192.168.2.0/24 comment="default configuration" dns-server=192.168.2.1,8.8.8.8 gateway=192.168.2.1 netmask=24
/ip dns
set allow-remote-requests=yes servers=192.168.2.1,8.8.8.8
/ip dns static
add address=192.168.88.1 name=router
/ip firewall filter
add action=accept chain=input comment="default configuration" protocol=icmp
add action=accept chain=input comment="default configuration" connection-state=established
add action=accept chain=input comment="default configuration" connection-state=related
add action=drop chain=input comment="default configuration" in-interface=ether1-gateway
/ip firewall nat
add action=masquerade chain=srcnat comment="default configuration" out-interface=ether1-gateway
/ip service
set api disabled=yes
/system clock
set time-zone-name=America/Chicago
/system identity
set name=ngMikrotik
/system leds
set 0 interface=wlan1
[admin@ngMikrotik] >
```
