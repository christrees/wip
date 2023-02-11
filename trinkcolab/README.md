Colabrative projects with Trink

[Edit](https://github.com/christrees/wip/edit/main/trinkcolab/README.md)

## Trink sync

### 2023.02.10 3pm PST 5pm CST - delay or reschedule
- [brave talk - 5:56PM](https://talk.brave.com/0eAINwV_92o3jMnzF9Ov5TWO421qxL1B0LADesA2VDQ)
- Monitor for trink and cat managed services
  - services logs (plex servers)
  - network, storage and compute health
- trink: firewall update
  - [https://gitea.trink.com/](https://gitea.trink.com/) working
  - [https://gitea.trink.com/trink/hx_phreak](https://gitea.trink.com/trink/hx_phreak) hx_phreak repo checkin
- cat: debating home assistant, new freenas, sort data, tuner channel mapps
  - [adb on FireTV](https://developer.amazon.com/docs/fire-tv/connecting-adb-to-device.html)
  - Drives 7x4TB(free-oldgh), 1x4TB(op-usb), 1x4TB(cattvwin10), 1x3TB(free-cat) 2x3TB(tnas), 1x2TB(tnas), 1x2TB(free-toshiba), 2x2TB(nsDiskStation),
  - ns 1TBssd 3x4TB pfsense truenas proxmox
  - bg 4x4TB DS411
  - backup google, amazon, apple, microsoft, github
  - [proxmox usb backup](https://ostechnix.com/backup-proxmox-to-usb-drive/)
  - [proxmox add usb drive](https://ostechnix.com/add-external-usb-storage-to-proxmox/)
  - [win11 on proxmox](https://youtu.be/2Ja_e6CMkNY?t=1743) to replace catwin10 at gh

### 2023.02.09 3pm PST 5pm CST - delay or reschedule
- [brave talk - online review delayed till trink relocates]()
- trink: pr update 
  - [pr auto merge issue](https://github.com/orgs/community/discussions/46757#discussioncomment-4913328)
- cat: tbd
  - update camera links [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
  - iptv and rstp integration to plex / home assistant
  - ns rebuild
  - cf storage map / drive inventory
  - cf storage backup and recovery document and test

### 2023.02.08 3pm PST 5pm CST
- [brave talk upated 4pm](https://talk.brave.com/TR7BD00ZoXdMc-RLfBMbXrNA8MTnxr1tlPnPClce_nk)
- trink: log replay main panic bug update
- cat: inventory
  - fix tnasplex port nat issue
  - build new system for grasshosre ?
  - backup nas maintainence plans ?
  - update [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)

### 2023.02.07 3pm PST 5pm CST
- [brave talk upated 5pm](https://talk.brave.com/njJc7hNWf5OT6QQsJlIWAj1cql5Yb0uUiHyP6cH_EKQ)
- trink: main panic bug update
- trink: hx-phreak repo ?
- trink: pfsense fix and backup
- cat: should backup and restore document pfsense for cf and gh
- cat: update [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
- cat: update [https://gh.2cld.net/docs/](https://gh.2cld.net/docs/)
  - look into spining up docker joomla mysql stack for magma
  - [ghMagma Install old doc](https://docs.google.com/document/d/1OMynAqcAFVLHyYkqTRr9BIQ2l7WvQnIka_QEcX6eXOc/edit)
  - [gh datacenter](https://docs.google.com/spreadsheets/d/1cPcjizKYg8XDHQctY8t1wBhW3g6rClCJ6O_DGaXIscI/edit#gid=1621592935)
  - [k8s on portainer](https://docs.portainer.io/admin/environments/add/kubernetes)
- tbd


### 2023.02.06 3pm PST 5pm CST
- [https://chat.christrees.com/](https://chat.christrees.com/) I may be online with Steve doing some grasshorse server stuff
- 

### 2023.02.05 3pm PST 5pm CST
- [brave talk]()
- trink: Review trink helix assci only Demo?
- cat: update [https://cf.christrees.com/ns/](https://cf.christrees.com/ns/)
  - move statrekDVR to nsDiskStation
  - cattvwin10 smb mount plexnsds M:
  - inspect tnasplex and dockerplex dvr sessions (seem to be working)
  - muck with channel mapping on tnasplex
  - [firetv recast file transfer](https://www.aftvnews.com/how-and-why-to-pull-video-recording-files-off-of-the-amazon-fire-tv-recast-dvr/)
  - [plex on synology and docker compose](https://www.wundertech.net/how-to-install-plex-on-a-synology-nas/)
  - [comskip github https://github.com/erikkaashoek/Comskip](https://github.com/erikkaashoek/Comskip)
  - [http://unixetc.co.uk/2020/03/16/how-to-install-comskip-on-a-raspberry-pi/](http://unixetc.co.uk/2020/03/16/how-to-install-comskip-on-a-raspberry-pi/)

### 2023.02.04 3pm PST 5pm CST
- [brave talk - created 4:55cst](https://talk.brave.com/f_cqVDp2n7hLESb3ss0U2w59FW9RdmjrD4QbTwPP2qo)
- trink: Review trink helix testbench Demo?
- cat: verify trinkdvr and trinktnas
  - CattvWin10:trinktnas plexlib on CattvWin10 N: SMB mount \\192.168.2.2\plexmedia which is \mnt\zpool-01\plexmedia\plexdvr\trinkdvr
  - CattvWin10:trinktvDVR  plexlib on CattvWin10 D:\trinktvDVR  - physical harddrive
  - CattvWin10:trinktvDVR recordings and future recordings are now on CattvWin10:trinknas
  - I don't see libs on Tri484 plex server
  - moved "Ghosts" and "So Help Me Todd" shows to Tnasplex:catdvr
  - Added both shows to Tnasplex ran into issue
  - When I added Ghost, I did one eps, went back to change it to all and it would not let me, deleted and attempted to re-add and it gave me an error
  - basically after I deleted it was still showing up in LiveTV guide when I attempted to add... probably cache issue ?
  - log out and back in on plex server... and I was able to re-add
  - had issue with tnasplex plex.tv connection can get to it fine on local subnet
  - firewall issues with plex in .2 subnet probably plex working on other ports on a session being blocked
  - not going to mess with much more figure the only issue would be remote view of tuner... use cattvwin10 for that for now
  - tbd
- cat: site maintaince schedule and checklist
  - tbd
- tbd

### 2023.02.03 3pm PST 5pm CST
- [brave talk](https://talk.brave.com/eiIGZbj5QJ7Z60sw10spTjwNghZjsXqeMrc2U7zb7Dk)
- Review trink helix testbench progress
- Chris: work on yesterday stuff
---
New stuff
- [SatIP Protocal](https://www.satip.info/sites/satip/files/resource/satip_specification_version_1_2_2.pdf)
- [plex iptv](https://www.videoconverterfactory.com/tips/plex-iptv.html)
- [iptv sw tuner for plex - github xteve-project](https://github.com/xteve-project/xTeVe)
- [xteve install documentation](https://github.com/xteve-project/xTeVe-Documentation/blob/master/en/configuration.md)
- [plex hdhomerun-api-use-udp-for-saving-streams](https://forums.plex.tv/t/hdhomerun-api-use-udp-for-saving-streams/162703)
- [Plex HDHomeRun Tuner API](https://forums.plex.tv/t/wrapping-other-video-cards-with-hdhomerun-apis/157792/6) helped me sort out how channel streams are managed
- [truenas cannot deploy plex](https://www.truenas.com/community/threads/truenas-scale-cannot-deploy-plex.100397/)
- half the time I cant get channel matching ui to save
- It's like certian channels will not save 074.10 075.1
- [plex docker on synology - good dockercompose file](https://www.wundertech.net/how-to-install-plex-on-a-synology-nas/)
- tbd

### 2023.02.02 3pm PST 5pm CST
- [brave talk](https://talk.brave.com/eiIGZbj5QJ7Z60sw10spTjwNghZjsXqeMrc2U7zb7Dk)
- Review trink helix testbench progress
- Chris: ~~finish USDA Survey,~~ look at 1099 tax stuff
- Chris: ~~fix tnasplex permissions issue~~
- Chris: ~~test tnasplex dvr~~
- Chris: Document docker volume mappings with ~~tnasplex app~~ and dockerplex
  - added pshare user UID 1000 and pshare group GID 1000
  - Use pshare user for smb login
  - Add apps (UID 568) to pshare group (this alone did not do it for plex app)
  - Changed plexmedia share to pshare owner and group 
  - Added User apps (UID 568) Allow | Special to plexmedia Dataset Permissions (this seemed to do it)
- Chris: review ns, gs and cf documents and merge
- Chris: document theory of plex.tv ip port / server stuff - netflix doing 30 day IP 'sign-on' per public IP
  - Seems servers are not unique, it is the public IP and port response
  - syncing info on each server to cloud and client... I think
- Chris: maybe [setup win11](https://youtu.be/2Ja_e6CMkNY) and ubuntu 22.04 on proxmox for gus remote testing
- Chris: update [https://gus.conversehouse.com/](https://gus.conversehouse.com/) on HD mappings and 5G backup route

### 2023.02.01 3pm PST 5pm CST
- [brave talk](https://talk.brave.com/eiIGZbj5QJ7Z60sw10spTjwNghZjsXqeMrc2U7zb7Dk)
- distroyed old nas setup true nas
- setup ssh to nas 24.149.22.11:2020 for rsync
- plex on truenas via k3s name: tnasplex
- plex volume issue on truenas [config access truenas-scale-cannot-deploy-plex](https://www.truenas.com/community/threads/truenas-scale-cannot-deploy-plex.100397/)
- review current [pr review request helix](https://github.com/helix-editor/helix/pull/5751#pullrequestreview-1277856760)
- review this doc and move to gitea.trink.com ??
- DanK band _HKH and the Imponderables_ [https://losaltosfirstfriday.org/](https://losaltosfirstfriday.org/)
- share tuner mapping with HD indication
- TrueNAS, Portainer, Tailscale example - [document](https://forum.level1techs.com/t/truenas-scale-ultimate-home-setup-incl-tailscale/186444) - [youtube](https://www.youtube.com/watch?v=R7BXEuKjJ0k)
- tbd

### 2023.01.30 3pm PST 5pm CST
- [brave talk](https://talk.brave.com/eiIGZbj5QJ7Z60sw10spTjwNghZjsXqeMrc2U7zb7Dk)
- setup ssh to nas 24.149.22.11:2020
- review [pr helix](https://github.com/helix-editor/helix/pull/5738)
- tbd

## Trink think things to review

- [Nestack for homelab](https://netstack.org/docs/)
   - Document trinktv home media model
   - Document storage sharing model
   - Docuemtn security storage model
- [Home Assistant](https://www.home-assistant.io/)
- [Home Assistant Release Review](https://www.youtube.com/watch?v=Ts-_BdFsvxI)
- [Home Assist Dashboard](https://www.youtube.com/watch?v=yy_GBQ5dhKw)
- [OpenSource security AI - frigate ai](https://github.com/blakeblackshear/frigate)
- [https://frigate.video/](https://frigate.video/)
- [Amazon Dash Button Rescure](https://blog.christophermullins.com/2019/12/20/rescue-your-amazon-dash-buttons/)
- [Amazon Dash Button Hack repo](https://github.com/Nekmo/amazon-dash)
- Setup Test network model on eve that models cf.lan and gh.lan
- Setup Test ipv6 network on eve

### TrinkCat Remote DataCenter
- It seem with robot simulation, plex dvr and transcode, OpenCI object recon ML and general AI having a DC with gpu is worth the effort.
- ProxMox server with shared GPU machine is my suggestion. [Proxmox vGPU Gaming Tutorial](https://www.youtube.com/watch?v=cPrOoeMxzu0)
    - Plex DVR and Transcoding.  There was about 30 stations
    - Private network extensions to Trink and Cat home TV networks using pfSense.
    - Remote rendering for robot simulations
    - Remote GPU and stoarge for AI/ML
- Grasshorse has lots of robot and robot kits.  
    - They had a grant for protomotion - stop motion animation robots
    - They have multiple robot kits: gantry robonova old school factory robot proto arms
- We chat about [https://www.coridium.us/coridium/shop](https://www.coridium.us/coridium/shop) 
    - BruceE company to integrate sensors into co.bot ?
    - MikeR did a lot of the embedded networking and they also did custom compilers for arm

## TrinkTV
Goal: Stable Plex server running in CF maintainable by mdt and cat.

### Plex Rebuilds 2022.08.12-14
Synopsys --
Use Window 10/11 with i5+ gen 10+ machine and map storage over network.

One of the ongoing issues is plex clients asking for transcode when its not required. 

[Avoid Plex transcoding](https://www.plexopedia.com/plex-media-server/general/avoid-transcoding/)

[Using GPU accelerated streaming](https://support.plex.tv/articles/115002178853-using-hardware-accelerated-streaming/)

Notes:
DVR recording takes very little cpu, but transcoding basically requries a gpu or lots of cores.
- macci - trink's old mini after rebuild would only playback to portals (aka portal client can take original format)
- trintv - old admin2cld-win10 Intel(R) Core(TM)2 Duo CPU E8400  @ 3.00GHz added trinks old video card and it could almost handle transcode to one web client
- HPi5 - Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz - laptop I've been using could almost handle 4 recording and playback HD streams to web clinets NOTE gen 10 so has GPU built in.
- catmini - i7 

## Robot Simulation
- Goal: Spider robot on table simulation running by both mdt and cat.
- Goal: Protomotion robot running simulation by both mdt and cat.

### Ubuntu setup catUbuntuVM 20.04
- [VirtualBox and Guest Package Download](https://www.virtualbox.org/wiki/Downloads) - Use Ubuntu 20.04 not 22.04
- [https://linuxconfig.org/install-virtualbox-guest-additions-on-linux-guest](https://linuxconfig.org/install-virtualbox-guest-additions-on-linux-guest)
  ```
   $ sudo apt update
   $ sudo apt install build-essential dkms linux-headers-$(uname -r)
  ```
- Set VM network card to Bridge
- [https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-20-04/](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-20-04/)
   ```
   sudo apt install openssh-server
   sudo systemctl status ssh
   lsb_release -a <- check that ubuntu is 20.04 for ros desktop package
   ```
- Setup git and [add ssh key to github](https://gist.github.com/xirixiz/b6b0c6f4917ce17a90e00f9b60566278)
  ```
  sudo apt install git
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
  xclip -sel clip < ~/.ssh/id_rsa.pub
  ```
- Paste key into your [github account settings](https://github.com/settings/keys) and test
  ```
  ssh -T git@github.com
  git remote set-url origin git@github.com:username/your-repository.git
  git add -A
  git commit -am "Update README.md"
  git push
  ```
- Visual Studio [Ubuntu install](https://code.visualstudio.com/docs/setup/linux)
- Remote-ssh and ROS extensions

### ROS setup
- [Setup ROS dev machine](https://www.youtube.com/watch?v=uWzOk0nkTcI)
- [https://articulatedrobotics.xyz/ready-for-ros-3-installing-ros/](https://articulatedrobotics.xyz/ready-for-ros-3-installing-ros/)
- [ROS distributions are linked to Ubuntu versions](https://www.reddit.com/r/ROS/comments/ufvrqg/i_always_get_the_error_unable_to_locate_package/)
  - Ubuntu 20.04 -> Noetic
  - Ubuntu 18.04 -> Melodic
  - Ubuntu 16.04 -> Kinetic
- [https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html)
  - Add ROS packages
  ```
  sudo apt update && sudo apt install curl gnupg2 lsb-release
  ```
  - Add ROS repo key
  ```
  sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
  ```
  - Add to package list
  ```
  echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  ```
  - Update Upgrade vm
  ```
  sudo apt update
  sudo apt upgrade
  ```
  - Install ROS desktop on catUbuntuVM desktop only
  ```
  sudo apt install ros-foxy-desktop
  ```
  - Install colcon
  ```
  sudo apt install python3-colcon-common-extensions
  ```
  - Add ROS to env
  ```
  echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
  ```
  - Add ROS xacro on catUbuntuVM desktop only
  ```
  sudo apt install ros-foxy-xacro ros-foxy-joint-state-publisher-gui
  ```

### Demo Robot 
- [https://articulatedrobotics.xyz](https://articulatedrobotics.xyz)
- [https://github.com/joshnewans/articubot_one](https://github.com/joshnewans/articubot_one)

#### Workspace setup and simulation
- [https://articulatedrobotics.xyz/mobile-robot-1-project-overview/](https://articulatedrobotics.xyz/mobile-robot-1-project-overview/)
- [https://articulatedrobotics.xyz/mobile-robot-3-concept-gazebo/](https://articulatedrobotics.xyz/mobile-robot-3-concept-gazebo/)
- Setup dev_ws for ROS Template and bot [https://github.com/joshnewans/articubot_one](https://github.com/joshnewans/articubot_one)
  - Create a directory dev_ws to use as a ROS workspace
  - Ccreate a directory called src  in dev_ws to put packages into
  - Clone our package from GitHub into src
  - Go back up to the workspace root and build it with colcon using the symlink-install 
  ```
    cat@catUbuntuVM:~/dev_ws$ mkdir src
    cat@catUbuntuVM:~/dev_ws$ cd src/
    cat@catUbuntuVM:~/dev_ws/src$ git clone https://github.com/joshnewans/articubot_one.git
    cat@catUbuntuVM:~/dev_ws/src$ ls
    articubot_one
    cat@catUbuntuVM:~/dev_ws/src$ cd ..
    cat@catUbuntuVM:~/dev_ws$ colcon build --symlink-install
    cat@catUbuntuVM:~/dev_ws$
    cat@catUbuntuVM:~/dev_ws$ source install/setup.bash
    cat@catUbuntuVM:~/dev_ws$ ros2 launch articubot_one launch_sim.launch.py
    cat@catUbuntuVM:~/dev_ws$ ros2 run teleop_twist_keyboard teleop_twist_keyboard
  ```
  

## Next Project research
- Digital Twins and Simulation
  - [Digital Twin and why it matters in IoT](https://www.networkworld.com/article/3280225/what-is-digital-twin-technology-and-why-it-matters.html)
  - [Defining a Digital Twin Platform](https://iskerrett.medium.com/defining-a-digital-twin-platform-de67586623de)
  - [Open API for Digital Twin](https://www.eclipse.org/ditto/http-api-doc.html#/)
- [AI build for dino game - https://blog.christrees.com/game/](https://blog.christrees.com/game/#dino-ai)
- [https://co.bot/](https://co.bot/)
  - [https://ros.org/](https://ros.org/)
  - [https://classic.gazebosim.org/tutorials?cat=guided_b&tut=guided_b1](https://classic.gazebosim.org/tutorials?cat=guided_b&tut=guided_b1)
  - [https://www.youtube.com/c/GazeboSim/videos](https://www.youtube.com/c/GazeboSim/videos)
  - [tbd]()
  - [tbd]()
- [NVidia Sigraph 2022](https://www.youtube.com/watch?v=Pev84SGO2r0)
  - [https://en.wikipedia.org/wiki/Universal_Scene_Description](https://en.wikipedia.org/wiki/Universal_Scene_Description)
  - [https://en.wikipedia.org/wiki/GlTF](https://en.wikipedia.org/wiki/GlTF)
  - [tbd]()
  - [tbd]()
