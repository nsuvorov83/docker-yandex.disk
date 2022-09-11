# Yandex.Disk Docker image

## How it works

1. Run container using interactive mode with mounted directory for configuration
1. Obtain OAuth token using your login and password
1. Stop container
1. Run container in daemon mode with mounted configuration directory which contains auth token

## Setup mode

```
docker run -it --rm --name yandex-disk -v yd-config:/root/.config/yandex-disk -v yd-data:/root/Yandex.Disk yandex-disk sh -c "yandex-disk --dir=/root/Yandex.Disk  setup"
```

## Daemon mode

```
docker run -d --restart always -v yd-config:/root/.config/yandex-disk -v yd-data:/root/Yandex.Disk yandex-disk sh -c "yandex-disk --dir=/root/Yandex.Disk start && tail -f /dev/null"
```
