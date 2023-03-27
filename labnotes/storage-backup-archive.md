[edit](https://github.com/christrees/wip/edit/main/labnotes/storage-backup-archive.md)
# Grasshorse project data lifecycle
based on [https://github.com/2cld/netstack/blob/master/docs/ops/backup/backup-diagram.md](https://github.com/2cld/netstack/blob/master/docs/ops/backup/backup-diagram.md)

- project active or creation of new project
```mermaid
sequenceDiagram
    participant artist
    participant magma
    participant projects
    participant garage
    participant parking
    participant lot in parking
    magma->>projects: project creation active
    artist->>projects: project changes
    projects->>projects: project zfs snapshot 2hr
    projects->>garage: project zfs sync daily
    garage->>garage: garage zfs snapshot weekly
    garage->>parking: garage zfs sync weekly
    parking->>parking: parking zfs snapshot monthly
```
- project inactive and/or project release
```mermaid
sequenceDiagram
    artist->>projects: project final changes
    artist->>magma: project final checkin
    magma->>projects: project dailies / reviews / final
    magma->>projects: project inactive
    projects->>garage: project zfs sync daily
    garage->>parking: garage zfs sync weekly
    parking->>lot in parking: project rsync archive
    parking->>magma: project archive parking lot assignment logs
```
- project hidden
```mermaid
sequenceDiagram
    magma->>projects: project hidden request process
    projects->>projects: project directory log and pointer update
    projects->>garage: active project remove data process
    garage->>garage: project directory log and pointer update
    garage->>parking: active project remove data process
    parking->>parking: project directory log and pointer update
    parking->>lot in parking: archive project confirmation check
    parking->>parking: archive project lot confirmation local
    parking->>magma: project hidden lot confirmation done
    parking->>magma: project archive parking lot assignment logs
```
- project archive resource reclaim
```mermaid
sequenceDiagram 
    magma->>projects: project storage reclaim
    projects->>projects: project storage reclaim process
    projects->>garage: project storage reclaim
    garage->>garage: project storage reclaim process
    garage->>parking: project storage reclaim
    parking->>lot in parking: project storage archive lot3 check
    parking->>parking: lot1 and lot2 check
    parking->>parking: lot volume mirror break and offline disk
    parking->>magma: project hidden lots offline done
```
