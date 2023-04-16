[edit](https://github.com/christrees/wip/edit/main/cfnetcleanup/README.md)

# cfnetcleanup

- A short guide to Comskip [http://www.kaashoek.com/files/manual.htm](http://www.kaashoek.com/files/manual.htm)
  ```
  comskip  “c:\My Videos\my film.mpg”
  ```
- Reduce hardware in cf network [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
  - ----
  - __DONE__ upgrade tnasplex via app upgrade on tnas [https://192.168.6.103:9090/](https://192.168.6.103:9090/) no issues
  - __DONE__ check 2020 ssh route test.christrees.com:2020
    - test.christrees.com:2020 -> IPv4 IP Address	24.149.22.11 [status_connection](http://192.168.6.1/#/html/status/status_connection.html)
    - 2020 to 2020	192.168.6.103 TCP	2020 to 2020	All IP Addresses [advancedportforwarding](http://192.168.6.1/#/html/advanced/security/advanced_security_advancedportforwarding.html)
    - 192.168.6.103 port 2020 to 192.168.2.2 port 22 ssh [http://192.168.2.1/firewall_nat.php](http://192.168.2.1/firewall_nat.php)
    - I think I'll just put trinktv at current tnasplex for now as he leaves nothing on this
  - __DONE__ Move Trink's plex recordings to tnasplex
    - stopped plex on cattvWin10 and dockerplex
    - nuked a lot of autherized clients to force a reload (did not nuke the ones I though were firetv)
    - moved NBC News to Tnas should recored to same place tonight 5:30 pm 2023.04.16
    - verified it recorded to catdvr ausi gold ep
  - TODO verify trink rsync
  - ----
  - TODO move data off tnas [https://192.168.6.103:9090/](https://192.168.6.103:9090/) 
  - TODO remove and replace or rebuild proxmox server with max mem and ?? GPU's ??
  - TODO remove cattvwin10 and replace with virtual windows server on proxmox
  - ---
- remove all plex servers except for bs01ds411 [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
  - ----
  - cattvwin10 at [http://test.christrees.com:32400/](http://test.christrees.com:32400/)
  - cattvwin10 at [http://192.168.6.180:32400/](http://192.168.6.180:32400/)
  - cattvwin10 at [http://10.147.17.1:32400/](http://10.147.17.1:32400/)
  - remote cattvWin10 
  - __status__ cattvwin10: running for trinktv access
  - ----
  - dockerplex at [http://test.christrees.com:32500/](http://test.christrees.com:32500/)
  - dockerplex at [http://192.168.6.103:32400](http://192.168.6.103:32400)
  - dockerplex at [http://192.168.2.103:32400/](http://192.168.2.103:32400/)
  - portainter admin dockerplex [http://192.168.6.103:9000/](http://192.168.6.103:9000/) and [http://192.168.2.103:9000/](http://192.168.2.103:9000/)
  - __status__ dockerplex: running no useage
  - ----
  - tnasplex at [http://test.christrees.com:32600/](http://test.christrees.com:32600/)
  - tnasplex at [http://192.168.6.103:32500/](http://192.168.6.103:32500/)
  - tnasplex at [http://192.168.2.103:32500/](http://192.168.2.103:32500/)
  - admin tnas for tnasplex [https://192.168.6.103:9090/](https://192.168.6.103:9090/) and [http://192.168.2.2/](http://192.168.2.2/)
  - __status__ tnasplex: running no useage
  - ----
- Verify bs02ds411 [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
  - ---
  - [https://www.plex.tv/](https://www.plex.tv/)
  - bs01ds411 at [http://test.christrees.com:32700/](http://test.christrees.com:32700/)
  - bs01ds411 at [http://192.168.6.105:32400](http://192.168.6.105:32400)
  - bs01ds411 at [http://192.168.2.105:32400](http://192.168.2.105:32400)
  - admin bs01ds411 at [http://192.168.2.105:5000/](http://192.168.2.105:5000/)
  - ---
- netstack document for docker container on proxmox
  - [https://netstack.org/docs/lan/compute/proxmox/](https://netstack.org/docs/lan/compute/proxmox/)
  - []()
  - []()
  - []()
- netstack document for plex docker container
  - [https://netstack.org/docs/lan/compute/proxmox/](https://netstack.org/docs/lan/compute/proxmox/)
  - []()
  - []()
  - []()
- netstack document for media storage map
  - []()
  - []()
  - []()
  - []()
- netstack document for docker GPU on proxmox
  - []()
  - []()
  - []()
  - []()

