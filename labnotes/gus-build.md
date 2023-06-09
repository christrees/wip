[edit](https://github.com/christrees/wip/edit/main/labnotes/gus-build.md)
## gus.lan backup build
- based on [tbd]()

## gus.lan local 192.168.252.0/24 gw [http://192.168.252.1/](http://192.168.252.1/) 

| web proxy    |   Link  | type | description |
|--------------|---------|------|-------------|
| spectrum | [https://24.217.248.77/](https://24.217.248.77/) | ??? | spectrum public IP gw |
|--------------|---------|------|-------------|
| Archer-C7 | [http://192.168.0.1/](http://192.168.0.1/) | static | tp-link gw |
| gus.lan | [http://192.168.252.1/](http://192.168.252.1/) | static | mikrotik gw |

- HOUSE DNS [http://192.168.0.1/HJHHETNAEUHIQKSA/userRpm/Index.htm](http://192.168.0.1/HJHHETNAEUHIQKSA/userRpm/Index.htm)
- gus.lan DNS [https://192.168.252.1/services_unbound.php](https://192.168.252.1/services_unbound.php}
- gus does not have control of this 24.217.248.77 cable modem
- [https://whatismyipaddress.com/](https://whatismyipaddress.com/) [https://whatismyipaddress.com/ip/24.217.248.77](https://whatismyipaddress.com/ip/24.217.248.77)


## 192.168.252.0/24 gw [http://192.168.252.1/](http://192.168.252.1/) dns 192.168.252.1
  
| web proxy    |   Link  | type | description |
|--------------|---------|------|-------------|
| ng.gus.lan | [https://192.168.252.1/](https://192.168.252.1/) | static | mikrotik ng on subnet |
| sg.gus.lan | [https://192.168.252.2/](https://192.168.252.2/) | static | truenas sg on subnet |
| cg.gus.lan | [https://192.168.252.3:8006/](https://192.168.252.3:8006/) | static | proxmox cg on subnet |
| sg2.gus.lan | [https://192.168.252.6/](https://192.168.252.6/) | static | truenas sg2 garage ? on subnet |
| lot.gus.lan | [https://192.168.252.12/](https://192.168.252.12/) | static | truenas log ? on subnet |
| ~~nginx default~~ | [http://192.168.2.103/](http://192.168.2.103/) | static | ~~default nginx proxy page running in portainer~~ |
| ~~nginx proxy admin~~ | [http://192.168.2.103:81](http://192.168.2.103:81) | macDHCP | ~~admin for nginx running in portainer~~ |
| ~~portainer admin~~ | [http://192.168.2.103:9000](http://192.168.2.103:9000) | macDHCP | portainer admin on proxmox docker 103 |
| ~~dockerplex web~~ | [http://192.168.2.103:32400](http://192.168.2.103:32400) | ~~macDHCP | 32400 on IP plex on portainer~~ |
| ~~tnasplex web~~ | [http://192.168.2.2:32500](http://192.168.2.2:32500) | static | ~~32500 on IP plex on portainer~~ |
| catghwin10 | [http://192.168.252.10](http://192.168.252.10) | static | windows 10 cat zt 10.147.17.127 |

- [https://my.zerotier.com/](https://my.zerotier.com/)
- tbd

---
---

## [cg network interfaces](https://192.168.252.3:8006/#v1:0:=node%2Fcg:4:11::::::) phy and virtio

| cg Name |   CIDR            |  gw          | pt/slv/brg  | ID   |  type          | description |
|---------|-------------------|--------------|-------------|------|----------------|-------------|
| eno1 | -                 | -            | -           | -    | Network Device | phy port left |
| enp11s0 | -                 | -            | -           | -    | Network Device | phy port right |
| vmbr0   | 192.168.252.3/23    | 192.168.253.254  | eno1     | -    | Linux Bridge   | vio bridge |
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
