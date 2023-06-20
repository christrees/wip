[edit]()
# gus-network

### sl.christrees.com (macci)

| web proxy    |   Link  | type | description |
|--------------|---------|------|-------------|
| Archer-C7 | [https://192.168.0.1/](https://192.168.0.1/) | static | tp-link ng on subnet |
| sl.christrees.com | [https://192.168.0.3:8006/](https://192.168.0.3:8006/) | static | proxmox sl on subnet |
| Nginx Proxy Manager | [http://192.168.0.3:81](http://192.168.0.3:81) | static | proxy sl on subnet |
| Homer | [https://192.168.252.13:8006/](https://192.168.252.13:8006/) | static | Homer sl on subnet |
| Portainer - Docker | [http://192.168.252.23:9000/](http://192.168.252.23:9000/) | static | portainer sl on subnet |
| Plex | [http://192.168.0.99:32400/web](http://192.168.0.99:32400/web) | static | Plex sl on subnet |

- proxmox using [https://netstack.org/docs/lan/compute/proxmox/](https://netstack.org/docs/lan/compute/proxmox/)
- docker portainer
  - ```
    bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/ct/docker.sh)"
    ```
  - [https://github.com/tteck/Proxmox/raw/main/ct/docker.sh](https://github.com/tteck/Proxmox/raw/main/ct/docker.sh)
### cg.gh.lan

| web proxy    |   Link  | type | description |
|--------------|---------|------|-------------|
| cg.gh.lan | [https://192.168.0.100:8006/](https://192.168.0.100:8006/) | static | proxmox sl on subnet |
| sg.gh.lan | [https://192.168.0.105:81/](https://192.168.0.105:81/) | static | proxmox sl on subnet |
| Homer | [https://192.168.252.13:8006/](https://192.168.252.13:8006/) | static | Homer sl on subnet |
| Portainer - Docker | [http://192.168.252.23:9000/](http://192.168.252.23:9000/) | static | portainer sl on subnet |
| Plex | [http://192.168.0.99:32400/web](http://192.168.0.99:32400/web) | static | Plex sl on subnet |

