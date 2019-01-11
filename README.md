### Usage

Extract media metadata to JSON format using FFmpeg

##### Build go app for linux (from mac)

```sh
CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -ldflags '-w' -o web ./main.go
```

##### Build/push container

```sh
docker build -t jweissig/alpine-ffprobe-detect .
docker push jweissig/alpine-ffprobe-detect
```

##### Run container

```sh
docker pull jweissig/alpine-ffprobe-detect
docker run -p 5000:5000 --rm jweissig/alpine-ffprobe-detect
```

##### Connect to localhost

http://localhost:5000/

##### Debugging

```sh
docker ps | grep ffprobe
docker exec -it <CONTAINER ID> bash
ffprobe -v quiet -print_format json -show_format -show_streams sample.mp3
```
