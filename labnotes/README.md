[edit](https://github.com/christrees/wip/edit/main/labnotes/README.md)

# WIP labnotes 
please clear before brain explodes
## subpages in labnotes
- [gus-build.md](./gus-build.md) gus's network docs
- [gh-build.md](./gh-build.md) based on [neststack proxmox](https://github.com/2cld/netstack/tree/master/docs/lan/compute/proxmox)
- [storage-backup-archive.md](./storage-backup-archive.md) based on [netstack backup](https://github.com/2cld/netstack/blob/master/docs/ops/backup/backup-diagram.md)
- [markdown-mermaid.md](./markdown-mermaid/)
- [mikrotik-test.md](./mikrotik-test/)
- [mikrotik-vrrp.md](./mikrotik-vrrp.md)


## quick notes
- document nginx proxy install
- [https://medium.com/@devops.ent/nginx-proxy-manager-how-to-installation-and-configuration-using-docker-portainer-1348c67a392e](https://medium.com/@devops.ent/nginx-proxy-manager-how-to-installation-and-configuration-using-docker-portainer-1348c67a392e)
- tbd
- verify documents in proxmox notes.. reflect in a 2cld repo ?
- get windows machine on proxmox
- zerotier to something inside wf
- remote config
- zerotier in linux container [zerotier-in-lxc-proxmox](https://forum.level1techs.com/t/zerotier-in-lxc-proxmox/155515/11)
- look at tailscale
- check firetv recast
- check gh catmedia transfers
- add drives to cg.wf.2cld.net


## ghNetworkMap [gh.2cld.net](https://gh.2cld.net/docs/ghNetworkMap)

## nsMikrotik [port forward](https://github.com/2cld/netstack/tree/master/docs/lan/compute/proxmox#nsmikrotik-port-forward)
## nsMikrotik [s/w](https://github.com/2cld/netstack/tree/master/docs/lan/compute/proxmox#nsmikrotik-sw)
## nsbuMikrotik [h/w](https://github.com/2cld/netstack/tree/master/docs/lan/compute/proxmox#nsbumikrotik-hw)
## VRRP on [hw and sw mikrotik](https://github.com/2cld/netstack/tree/master/docs/lan/compute/proxmox#vrrp-on-hw-and-sw-mikrotik)
- [https://help.mikrotik.com/docs/display/ROS/VRRP+Configuration+Examples](https://help.mikrotik.com/docs/display/ROS/VRRP+Configuration+Examples)

## proxmox install mikrotik CHR on a Proxmox
- [Virtual Network in Proxmox for MPTCP Test lab](https://www.youtube.com/watch?v=S-Xmcig1ddA)
- [https://ostechnix.com/import-qcow2-into-proxmox/](https://ostechnix.com/import-qcow2-into-proxmox/)
- [https://wiki.mikrotik.com/wiki/Manual:CHR_ProxMox_installation](https://wiki.mikrotik.com/wiki/Manual:CHR_ProxMox_installation)
- [https://mikrotik.com/download](https://mikrotik.com/download)
- [https://dailymikrotik.blogspot.com/2015/08/commands-in-mikrotik-router-os.html](https://dailymikrotik.blogspot.com/2015/08/commands-in-mikrotik-router-os.html)
- [https://forum.proxmox.com/threads/vm-disk-location-cant-find-the-vm-disk.101118/](https://forum.proxmox.com/threads/vm-disk-location-cant-find-the-vm-disk.101118/)
- downloaded raw disk image chr-7.8.img.zip
- reference [https://gregsowell.com/?p=6051](https://gregsowell.com/?p=6051)
1. Go to the mikrotik download page (above) and grab the raw disk image chr-7.8.img.zip
2. Extract the img file and transfer it into your proxmox /root folder.
3. On proxmox issue the following “qm list”. Pick the next sequential number that isn’t already taken.
4. Create the directory for this VM: “mkdir /var/lib/vz/images/150”
5. Create the qcow2 image. Adjust the image name “/root/chr-6.44.3.img” to whatever you downloaded and adjust the VM number from 150 to whatever you choose “/var/lib/vz/images/150/vm-150-disk-1.qcow2”
```bash
qemu-img convert \
-f raw \
-O qcow2 \
/root/chr-6.44.3.img \
/var/lib/vz/images/150/vm-150-disk-1.qcow2
```
```bash
qm create 101 --name ngMikrotik --net0 virtio,bridge=vmbr1 --bootdisk virtio0 --ostype l26 --memory 256 --onboot no --sockets 1 --cores 1 --virtio0 local:101/vm-101-disk-1.qcow2
```
6. Create the VM inside of proxmox. Be sure to change the VM number “150” in all lines to yours and also adjust the name to whatever you prefer:
```bash
qm create 150 \
–name chr-cust1 \
–net0 virtio,bridge=vmbr0 \
–bootdisk virtio0 \
–ostype l26 \
–memory 256 \
–onboot no \
–sockets 1 \
–cores 1 \
–virtio0 local:150/vm-150-disk-1.qcow2
```
```bash
qm create 101 --name ngMikrotik --net0 virtio,bridge=vmbr1 --bootdisk virtio0 --ostype l26 --memory 256 --onboot
no --sockets 1 --cores 1 --virtio0 local:101/vm-101-disk-1.qcow2
```
### Enable mikrotik on proxmox local
- Enable images on cg local
  - Datacenter -> Storage -> local -> Edit Add "Disk image"
- Create qcow template directory
```bash
root@cg:~# mkdir /var/lib/vz/template/qcow/
```
- convert image
```bash
root@cg:~# qemu-img convert -f raw -O qcow2 /var/lib/vz/template/iso/chr-7.8.img /var/lib/vz/template/qcow/mikrotik-chr-7-8.qcow2
```
- Create vm without drive
```bash
qm create 101 --name ngMikrotik --net0 virtio,bridge=vmbr1 --bootdisk virtio0 --ostype l26 --memory 256 --onboot
no --sockets 1 --cores 1 
```
- Import qcow disk image
```bash
root@cg:~# cd /var/lib/vz/template/qcow/
root@cg:/var/lib/vz/template/qcow# qm importdisk 101 mikrotik-chr-7-8.qcow2 local
importing disk 'mikrotik-chr-7-8.qcow2' to VM 101 ...
Formatting '/var/lib/vz/images/101/vm-101-disk-0.raw', fmt=raw size=134217728 preallocation=off
transferred 0.0 B of 128.0 MiB (0.00%)
transferred 6.7 MiB of 128.0 MiB (5.21%)
transferred 127.0 MiB of 128.0 MiB (99.21%)
transferred 128.0 MiB of 128.0 MiB (100.00%)
transferred 128.0 MiB of 128.0 MiB (100.00%)
Successfully imported disk as 'unused0:local:101/vm-101-disk-0.raw'
root@cg:/var/lib/vz/template/qcow#
```
7. Login and verify

## proxmox firewall [proxmox cg node https://192.168.2.3:8006/](https://192.168.2.3:8006/)
- [proxmox-user-management](https://pve.proxmox.com/wiki/User_Management)
- [proxmox-firewall-youtube](https://www.youtube.com/watch?v=yA9e7A9v7Xc)
- [proxmox-NAT](https://bobcares.com/blog/setup-nat-on-proxmox/)
- [proxmox-firewall-docs](https://pve.proxmox.com/wiki/Firewall)
- [datacenter firewall https://192.168.2.3:8006/#v1:0:18:4:::::::32](https://192.168.2.3:8006/#v1:0:18:4:::::::32)
- tracert from cmd - CTRL+C will send a break (stop execution) when no text is selected
```powershell
tracert cf.christrees.com
```
- [rackn.io provision on proxmox](https://docs.rackn.io/en/latest/doc/content-packages/proxmox.html)

## proxmox install doc sync
- [https://netstack.org/docs/lan/compute/proxmox/](https://netstack.org/docs/lan/compute/proxmox/)
- [https://gh.2cld.net/docs/proxmox/](https://gh.2cld.net/docs/proxmox/)
- [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)

## proxmox windows11 vm nswin11 [moved here](https://github.com/2cld/netstack/blob/master/docs/lan/compute/proxmox/nswin11vm.md)

## zerotier 
- zerotier [https://www.zerotier.com/download/](https://www.zerotier.com/download/)
- [zerotier on synology](https://docs.zerotier.com/devices/synology/)
- [zerotier on mikrotik download ARM64 extra packages](https://mikrotik.com/download)
- [zerotier on mikrotik help docs](https://help.mikrotik.com/docs/display/ROS/ZeroTier)

## iso rip
- bash "dd if=/dev/sr0 of=name_of_dvd.iso"
- [dvd_ripping_in_2019](https://www.reddit.com/r/DataHoarder/comments/cse88w/dvd_ripping_in_2019/)
- makeMKV Handbrake AnyDVD DVDFab 
- [https://b3n.org/automatic-ripping-machine/](https://b3n.org/automatic-ripping-machine/)
- [https://github.com/donmelton/video_transcoding](https://github.com/donmelton/video_transcoding)
- [https://hub.docker.com/r/jlesage/makemkv/](https://hub.docker.com/r/jlesage/makemkv/)
- [https://github.com/automatic-ripping-machine/automatic-ripping-machine](https://github.com/automatic-ripping-machine/automatic-ripping-machine)

## QNAP
- QNAP TS-431 [amazon QNAP-TS-431P-US-Cortex-1-7GHzDual](https://www.amazon.com/QNAP-TS-431P-US-Personal-Cortex-1-7GHzDual/dp/B01N2K147Q)

## plex data sort
- [https://wip.christrees.com/cfnetcleanup/plexdatasort](https://wip.christrees.com/cfnetcleanup/plexdatasort)
- tbd


## review
- [OpenSource security AI - frigate ai](https://github.com/blakeblackshear/frigate)
- [https://frigate.video/](https://frigate.video/)
- [Amazon Dash Button Rescure](https://blog.christophermullins.com/2019/12/20/rescue-your-amazon-dash-buttons/)
- [Amazon Dash Button Hack repo](https://github.com/Nekmo/amazon-dash)

## home assistant [https://netstack.org/docs/portals/homeassistant/](https://netstack.org/docs/portals/homeassistant/)
- [ha on synology](https://www.home-assistant.io/installation/alternative/#synology-nas)

### cameras
- [https://blinkforhome.com/blink-app](https://blinkforhome.com/blink-app)
- [Using WyzeCam in Home Assistant (with RTSP firmware)](https://www.youtube.com/watch?v=RD6K30ftV24)
- [How to add Zmodo cameras to Zoneminder and monitor with Home Assistant](https://www.youtube.com/watch?v=3L9_in6LciY&t=116s)
= [tbd]()

## plex [https://netstack.org/docs/portals/plex/](https://netstack.org/docs/portals/plex/)

## stoarge [https://netstack.org/docs/lan/storage/freenas/](https://netstack.org/docs/lan/storage/freenas/)
- [zfs-should-belong-to-proxmox-or-truenas](https://forum.proxmox.com/threads/looking-for-advise-zfs-should-belong-to-proxmox-or-truenas.98129/)
- [http://192.168.2.105/](http://192.168.2.105/) bs01ns411
- [synology fan fail fix](https://www.reddit.com/r/synology/comments/bc90fk/synology_cpu_fan_mainboard_failure_simple/)
- [tailscale on synology](https://www.wundertech.net/how-to-set-up-tailscale-on-a-synology-nas/)
- [ceph cluster on proxmox](https://packetpushers.net/proxmox-ceph-full-mesh-hci-cluster-w-dynamic-routing/)
- [tbd]()

## pfsense [https://netstack.org/docs/lan/network/pfsense/](https://netstack.org/docs/lan/network/pfsense/)
- [https://www.tecmint.com/how-to-setup-failover-and-load-balancing-in-pfsense/](https://www.tecmint.com/how-to-setup-failover-and-load-balancing-in-pfsense/)

## backup
- [backup](https://netstack.org/docs/ops/backup/)
- [backup powershell script](https://netstack.org/docs/ops/backup/backup-powershell-script)
- [robocopy backup for powershell](https://netstack.org/docs/ops/backup/#robocopy)

---
the end
