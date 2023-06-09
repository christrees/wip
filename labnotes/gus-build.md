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


### DHCP 2023.06.09
```
ID	Client Name	MAC Address	Assigned IP	Lease Time
1	TIVO-748000190569948	00-11-D9-35-02-A8	192.168.0.111	01:10:29
2	KathysRokuUltra	84-EA-ED-A8-64-91	192.168.0.100	01:10:22
3	TIVO-8480001902B1749	00-11-D9-5F-47-82	192.168.0.107	01:10:30
4	android-4de9db6d80c2f04c	AC-D0-74-13-A8-78	192.168.0.105	01:32:15
5	TIVO-8480001902B1749	00-11-D9-5F-47-83	192.168.0.114	01:10:31
6	TIVO-74600019083B6E2	00-11-D9-38-0B-FC	192.168.0.116	01:10:29
7	Portal-AF5234A58F2A	A4-0E-2B-2D-67-85	192.168.0.103	01:10:52
8	Unknown	08-AA-55-41-1F-18	192.168.0.102	01:12:47
9	Portal-8B57B421F784	A4-0E-2B-4C-EF-C7	192.168.0.104	01:10:50
10	Unknown	C6-9A-1C-84-72-48	192.168.0.110	01:36:56
11	Unknown	1A-64-1A-7E-00-3D	192.168.0.108	01:55:41
12	MikroTik	D4-CA-6D-7C-E6-52	192.168.0.106	01:53:12
13	StevesRokuUltra	8C-49-62-0B-69-8D	192.168.0.109	01:29:22
14	amazon-c7d67c84b	18-74-2E-B3-27-15	192.168.0.118	01:08:36
15	Unknown	16-2F-4E-27-3D-1F	192.168.0.120	00:39:20
16	Unknown	A4-08-01-60-57-35	192.168.0.117	01:39:06
17	Unknown	D2-A8-EA-4A-28-E8	192.168.0.101	01:45:41
18	A6386161	7C-B5-66-05-9D-C6	192.168.0.115	01:05:00
19	LGwebOSTV	7C-1C-4E-5D-C5-F6	192.168.0.124	01:19:09
```
#### 5g
```
ID	MAC Address	Current Status	Received Packets	Sent Packets
1	A4-0E-2B-4C-EF-C7	STA-ASSOC	352779	325800
2	C6-9A-1C-84-72-48	STA-ASSOC	152531	298993
3	18-74-2E-B3-27-15	STA-ASSOC	133790	810785
4	1A-64-1A-7E-00-3D	STA-ASSOC	133530	619078
5	7C-B5-66-05-9D-C6	STA-ASSOC	612186	598275
6	16-2F-4E-27-3D-1F	STA-ASSOC	2079	1707
7	7C-1C-4E-5D-C5-F6	STA-ASSOC	10942	10024
```
#### 2.4g
```
ID	MAC Address	Current Status	Received Packets	Sent Packets
1	AC-D0-74-13-A8-78	STA-ASSOC	13490574	6905402
2	D2-A8-EA-4A-28-E8	STA-ASSOC	3042	2023
```

---

- ventory USB boot [https://www.ventoy.net/](https://www.ventoy.net/)
- proxmox pve 7.4 [https://www.proxmox.com/en/downloads/category/iso-images-pve](https://www.proxmox.com/en/downloads/category/iso-images-pve)
- truenas scale [https://www.truenas.com/download-truenas-scale/](https://www.truenas.com/download-truenas-scale/)

---

- tbd
