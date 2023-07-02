sorting out plex and plexdata

## bring down dockerplex
- [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
- dockerplex plex page [http://192.168.6.103:32400/](http://192.168.6.103:32400/)
- proxmox admin page [https://192.168.6.103:8006/](https://192.168.6.103:8006/)
- docker container Summary [https://192.168.6.103:8006/#v1:0:=lxc%2F103:4:::::::](https://192.168.6.103:8006/#v1:0:=lxc%2F103:4:::::::)
- portainer admin page [http://192.168.6.103:9000/#!/auth](http://192.168.6.103:9000/#!/auth)
- volumes in portainer local env [http://192.168.6.103:9000/#!/2/docker/volumes](http://192.168.6.103:9000/#!/2/docker/volumes)
- CT-103 (docker) -> Console to find the volumes mapped into plex via portainer
```
root@docker ~# ls -alu /var/lib/docker/volumes/
total 52
drwx-----x  7 root root  4096 Feb 20 19:44 .
drwx--x--- 13 root root  4096 Feb 20 19:44 ..
-rw-------  1 root root 32768 Jan 29 00:24 metadata.db
drwx-----x  3 root root  4096 Jan 17 23:52 plexConfig
drwx-----x  3 root root  4096 Jan 30 21:11 plexDVR
drwx-----x  3 root root  4096 Jan 16 03:09 plexMovies
drwx-----x  3 root root  4096 Jan 17 23:50 portainer_data
drwx-----x  3 root root  4096 Jan 30 21:10 zfs2tbplexdvr
root@docker ~# ls -alu /var/lib/docker/volumes/plexDVR/
total 12
drwx-----x 3 root root 4096 Feb 20 19:44 .
drwx-----x 7 root root 4096 Feb 20 19:44 ..
drwxr-xr-x 7 1000 1000 4096 Feb  3 00:20 _data
root@docker ~# ls -alu /var/lib/docker/volumes/plexDVR/_data/
total 28
drwxr-xr-x 7 1000 1000 4096 Feb 20 19:44  .
drwx-----x 3 root root 4096 Feb 20 19:44  ..
drwxr-xr-x 2 1000 1000 4096 Feb 20 04:43  .grab
drwxr-xr-x 3 1000 1000 4096 Jan 20 02:03 'Ghosts (2021)'
drwxr-xr-x 3 1000 1000 4096 Jan 16 23:03 'MacGyver (1985)'
drwxr-xr-x 4 1000 1000 4096 Jan 16 22:33 'Mom (2013)'
drwxr-xr-x 3 1000 1000 4096 Jan 17 00:03 'The A-Team (1983)'
root@docker ~#
```
- rsync -rv -e ‘ssh -p 2020’ /var/lib/docker/volumes/plexDVR/_data/ buadmin@192.168.2.105:/volume1/pshare/bs01DVR/
- [tbd]()

## plex storage sort
- setup ds211j to (storageserver ds211j) ssds211j 192.168.6.159 nsadmin What#Time disable admin setup sshauthkey
- map out storage for plex dvr
  - target ds411 for plex storage
  - target ds211j for temp trink dvr ? not sure
  - setup rsync
- attempt all tuners to one plex and attempt recording 8 streams to see if it breaks
- move trinkdvr off cattvwin10
- move ssh target

## rsync setup for plex dvr
- setup buadmin user on bu01ds411 192.168.2.105
- enable ssh on bu01ds411 
- enable rsync on bu01ds411
- ebable user buadmin to use rsync
- setup ssh keys [ssh key config](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server)
  - ghadmin@cattvWin10:~$ ssh-keygen
  - ghadmin@cattvWin10:~$ ssh-copy-id buadmin@192.168.2.105
- rsync -rv --chown=mdt:972 -e 'ssh -p 2020' trink@test.christrees.com:/mnt/zpool-01/plex/ /mnt/data/media/video/dvr/
- rsync -rv -e 'ssh -p 2020' "/mnt/d/cattvDVR/Resident Alien (2021)/" buadmin@192.168.2.105:/volume1/pshare/tvNew/
- buadmin@bs01ds411:/volume1/pshare$ mv tvNew "Resident Alien (2021)"
- buadmin@bs01ds411:/volume1/pshare$ chown -R plex Resident\ Alien\ \(2021\)/
- buadmin@bs01ds411:/volume1/pshare$ mkdir tvNew
- buadmin@bs01ds411:/volume1/pshare$ mv Resident\ Alien\ \(2021\)/ tvNew/
- buadmin@bs01ds411:/volume1/pshare/tvNew$ mkdir ghosts
- buadmin@bs01ds411:/volume1/pshare/tvNew$ mkdir sheldon
- buadmin@bs01ds411:/volume1/pshare/tvNew$ mkdir nightcourt
- buadmin@bs01ds411:/volume1/pshare/tvNew$ mkdir qleap
- buadmin@bs01ds411:/volume1/pshare/tvNew$ mkdir shmtodd
- rsync -rv -e 'ssh -p 2020' /mnt/d/cattvDVR/Ghosts\ \(2021\)/ buadmin@192.168.2.105:/volume1/pshare/tvNew/ghosts/
- rsync -rv -e 'ssh -p 2020' /mnt/d/cattvDVR/Young\ Sheldon\ \(2017\)/ buadmin@192.168.2.105:/volume1/pshare/tvNew/sheldon/
- rsync -rv -e 'ssh -p 2020' /mnt/d/cattvDVR/Night\ Court\ \(2023\)/ buadmin@192.168.2.105:/volume1/pshare/tvNew/nightcourt/
- rsync -rv -e 'ssh -p 2020' /mnt/d/cattvDVR/Quantum\ Leap\ \(2022\)/ buadmin@192.168.2.105:/volume1/pshare/tvNew/qleap/
- rsync -rv -e 'ssh -p 2020' /mnt/d/cattvDVR/So\ Help\ Me\ Todd\ \(2022\)/ buadmin@192.168.2.105:/volume1/pshare/tvNew/shmtodd/
```
buadmin@bs01ds411:/volume1/pshare/tvNew$ mv shmtodd/ "So Help Me Todd (2022)"
buadmin@bs01ds411:/volume1/pshare/tvNew$ sudo chown -R plex So\ Help\ Me\ Todd\ \(2022\)/
buadmin@bs01ds411:/volume1/pshare/tvNew$ mv qleap/ "Quantum Leap (2022)"
buadmin@bs01ds411:/volume1/pshare/tvNew$ sudo chown -R plex Quantum\ Leap\ \(2022\)/
buadmin@bs01ds411:/volume1/pshare/tvNew$ mv nightcourt/ "Night Court (2023)"
buadmin@bs01ds411:/volume1/pshare/tvNew$ sudo chown -R plex Night\ Court\ \(2023\)/
buadmin@bs01ds411:/volume1/pshare/tvNew$ mv sheldon/ "Young Sheldon (2017)"
buadmin@bs01ds411:/volume1/pshare/tvNew$ sudo chown -R plex Young\ Sheldon\ \(2017\)/
buadmin@bs01ds411:/volume1/pshare/tvNew$ mv ghosts/ "Ghosts (2021)"
buadmin@bs01ds411:/volume1/pshare/tvNew$ sudo chown -R plex Ghosts\ \(2021\)/
```
- rsync -rv -e 'ssh -p 2020'  /mnt/d/cattvDVR/Hogan* buadmin@192.168.2.105:/volume1/pshare/tvOld/
- rsync -rv -e 'ssh -p 2020'  /mnt/d/cattvDVR/Accord* buadmin@192.168.2.105:/volume1/pshare/tvOld/
- rsync -rv -e 'ssh -p 2020'  /mnt/d/cattvDVR/That* buadmin@192.168.2.105:/volume1/pshare/tvOld/
- rsync -rv -e 'ssh -p 2020'  /mnt/d/cattvDVR/Rick* buadmin@192.168.2.105:/volume1/pshare/tvAnew/
- rsync -rv -e 'ssh -p 2020'  /mnt/d/cattvDVR/Bob* buadmin@192.168.2.105:/volume1/pshare/tvAnew/
- rsync -rv -e 'ssh -p 2020'  /mnt/d/cattvDVR/King* buadmin@192.168.2.105:/volume1/pshare/tvAold/
