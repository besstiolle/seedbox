# seedbox
Docker Templates for Seedbox management + Sonarr/Radarr/...

## How run it

### Image Rtorrent 

#### Build

```
cd rtorrent
docker build -t seedbox/rtorrent:0.0.1 .
```

#### Run

_MY_DIRECTORY_ must be setted

```
docker run --mount type=bind,source=/C/_MY_DIRECTORY_/mount/download,target=/root/rtorrent/download --mount type=bind,source=/C/_MY_DIRECTORY_/mount/session,target=/root/rtorrent/session --mount type=bind,source=/C/_MY_DIRECTORY_/mount/watch,target=/root/rtorrent/watch --mount type=bind,source=/C/_MY_DIRECTORY_/mount/log,target=/root/rtorrent/log seedbox/rtorrent:0.0.1 
```

#### Check health

```
docker inspect --format="{{json .State.Health.Status}}" _ID_
```


## Clean install
