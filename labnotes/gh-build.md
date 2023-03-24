[edit](https://github.com/christrees/wip/edit/main/labnotes/gh-build.md)
## gh backup build

## gh.lan local 192.168.254.0/24 gw [http://192.168.254.254/](http://192.168.254.254/) 

| web proxy    |   Link  | type | description |
|--------------|---------|------|-------------|
| 0028.ftth.farmtel.net | [https://208.126.60.28/](https://208.126.60.28/) | static | farmtel public IP |
|--------------|---------|------|-------------|
| farmtel | [http://192.168.254.254/](http://192.168.254.254/) | static | farmtel gw |
| gh.lan | [http://192.168.254.1/](http://192.168.254.1/) | static | gh ns gw |
| projects | [http://192.168.254.6/](http://192.168.254.6/) | dhcp-res | ns gw |
| magma | [http://192.168.6.103/](http://192.168.6.103/) | dhcp-res | gh portal |

- IPA DNS [https://192.168.254.1/status_dhcp_leases.php](https://192.168.254.1/status_dhcp_leases.php)
- IPA DNS binds [https://192.168.254.1/services_unbound.php](https://192.168.254.1/services_unbound.php}
- gh does not have control of this gw router 208.126.60.28
- [https://whatismyipaddress.com/](https://whatismyipaddress.com/) [https://whatismyipaddress.com/ip/208.126.60.28](https://whatismyipaddress.com/ip/208.126.60.28)
- IPA [http://192.168.254.254/advancedsetup_dhcpreservation.html](http://192.168.254.254/advancedsetup_dhcpreservation.html)
- DNS pfsense [http://192.168.254.1](http://192.168.254.254/) route to 192.168.252.0/23 subnet


## 192.168.252.0/23 gw [http://192.168.252.1/](http://192.168.252.1/) dns 192.168.253.254
  
| web proxy    |   Link  | type | description |
|--------------|---------|------|-------------|
| ng.gh.lan | [https://192.168.253.254/](https://192.168.253.254/) | static | pfsense ng on subnet |
| sg.gh.lan | [https://192.168.252.2/](https://192.168.252.2/) | static | truenas sg on subnet |
| cg.gh.lan | [https://192.168.252.3:8006/](https://192.168.252.3:8006/) | static | proxmox cg on subnet |
| ~~nginx default~~ | [http://192.168.2.103/](http://192.168.2.103/) | static | ~~default nginx proxy page running in portainer~~ |
| ~~nginx proxy admin~~ | [http://192.168.2.103:81](http://192.168.2.103:81) | macDHCP | ~~admin for nginx running in portainer~~ |
| portainer admin | [http://192.168.2.103:9000](http://192.168.2.103:9000) | macDHCP | portainer admin on proxmox docker 103 |
| ~~dockerplex web~~ | [http://192.168.2.103:32400](http://192.168.2.103:32400) | ~~macDHCP | 32400 on IP plex on portainer~~ |
| ~~tnasplex web~~ | [http://192.168.2.2:32500](http://192.168.2.2:32500) | static | ~~32500 on IP plex on portainer~~ |
| nswin11 | [http://192.168.2.195](http://192.168.2.195) | static | windows 11 vm-400 |

## proxmox [https://192.168.252.3:8006/](https://192.168.252.3:8006/) phy and virtio

| cg Name |   CIDR            |  gw          | pt/slv/brg  | ID   |  type          | description |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| enp60f0 | -                 | -            | -           | -    | Network Device | phy port left |
| enp60f1 | -                 | -            | -           | -    | Network Device | phy port right |
| vmbr0   | 192.168.2.3/24    | 192.168.2.1  | enp60f0     | -    | Linux Bridge   | vio bridge |
| vmbr1   | 192.168.254.0/24  | -            | enp60f1     | -    | Linux Bridge   | vio bridge |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| __ct-100__  | ssh -p 22 admin@192.168.2.100 |  gw          | pt/slv/brg  | ID   |  type          | description |
| eth0    | 192.168.2.100/24  | 192.168.2.1  | vmbr0       | net0 | ct-100 eth0    | ct-100 (ubuntu) eth0 |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| __ct-103__  | ssh -p 22 admin@192.168.2.103 |  gw          | pt/slv/brg  | ID   |  type          | description |
| eth0    | 192.168.2.103/24  | 192.168.2.1  | vmbr0       | net0 | ct-103 eth0    | ct-103 (docker) eth0 |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| __vm-101__  | ssh -p 22 admin@192.168.2.4 |  gw          | pt/slv/brg  | ID   |  type          | description |
| ether1  | 192.168.2.4/24    | 192.168.2.1  | vmbr1       | net0 | vm-101 ether1  | vm-101 (ngMiktrotik) ether1 |
| ether2  | 192.168.254.195/24| -            | vmbr1       | net1 | vm-101 ether2  | vm-101 (ngMiktrotik) ether2 |
| ether3  | -                 | -            | vmbr0       | net2 | vm-101 ether3  | vm-101 (ngMiktrotik) ether3 |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| __vm-102__  | ssh -p 22 admin@192.168.2.2 |  gw          | pt/slv/brg  | ID   |  type          | description |
| ether1  | 192.168.2.4/24    | 192.168.2.1  | vmbr1       | net0 | vm-101 ether1  | vm-101 (truenas) ether1 |
| ether2  | -                 | -            | vmbr1       | net1 | vm-101 ether2  | vm-101 (truenas) ether2 |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| __vm-400__  | ssh -p 22 admin@192.168.2.4 |  gw          | pt/slv/brg  | ID   |  type          | description |
| ether1  | 192.168.2.4/24    | 192.168.2.1  | vmbr1       | net0 | vm-101 ether1  | vm-101 (ngMiktrotik) ether1 |

- ubuntu 192.168.2.100
  ```
  ssh -p 22 admin@192.168.2.100
  ```
- docker 
  ```
  ssh -p 22 admin@192.168.2.103
  ``` 
  - portainer ui [http://192.168.2.103:9000](http://192.168.2.103:9000)
- nsMikrotik
  - lan-> 192.168.2.4
  ```
  ssh -p 22 admin@192.168.2.4
  ``` 
  - wan-> 192.168.254.195
  ```
  ssh -p 22 admin@192.168.254.195
  ```
  
- [https://netstack.org/docs/lan/compute/proxmox/](https://netstack.org/docs/lan/compute/proxmox/)

- [ASUS P9X79_WS - Motherboard](https://www.asus.com/Commercial-Servers-Workstations/P9X79_WS/overview/) [video](https://www.youtube.com/watch?v=W8jogtOzw6Y)
- [Gigabyte GV-N660OC-2GD NVIDIA GeForce GTX 660 GPU](https://www.gigabyte.com/Graphics-Card/GV-N660OC-2GD#ov)
- [G.SKILL 16GB 2x 8GB DDR3 OC 2400MHz PC3-19200U 240Pin](https://www.gskill.com/product/165/173/1532068057/F3-2400C10D-16GTX)

---

- ventory USB boot [https://www.ventoy.net/](https://www.ventoy.net/)
- proxmox pve 7.4 [https://www.proxmox.com/en/downloads/category/iso-images-pve](https://www.proxmox.com/en/downloads/category/iso-images-pve)
- truenas scale [https://www.truenas.com/download-truenas-scale/](https://www.truenas.com/download-truenas-scale/)

---

- tbd
