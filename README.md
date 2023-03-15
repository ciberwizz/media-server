# media-server
Compose for Jellyfin + Sonarr + Radarr + Jackett + Radarr + qbittorrent


Recomend putting these services behind a vpn, tailscale is awesome and is a mesh vpn so it will use local resources if available


## run
``` 
$ podman-compose up -d
```

## configure

### Jellyfin
set root folder

### Jackett 
port: 9117
Jackett is a torrent search for multi tracker

add the tracker you like/want

### Sonarr/Radarr
ports: 7878/8989
manage Movies and series

Add root folder that is in the shared volume

add indexers: 
- use jackett api key 
- instead of using a link for each tracker use the aggregation api:
    http://jackett:9117/api/v2.0/indexers/test:passed/results/torznab/
- setup download clients: qbittorrent default user/pass: admin/adminadmin

### Bazaar
port:6767
Fetch subtitles

- root folder
- setup default languages
- connection with sonarr and radarr
- set providers (recommend: Opensubtiles.com/org, embedded, yify)

### qbittorrent
port:8080
