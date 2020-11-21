# 実行までの流れ

## VMを起動

```
vagrant up
```

## VMの中に入る

```
vagrant ssh
```

## dockerを起動

```
sudo systemctl start docker
```

## docker-bench-securityをpull

```
docker pull docker/docker-bench-security
```

## スキャンしたいコンテナをあげる

```
docker run --rm -d nginx
```

## スキャン実行

```
docker run --rm --net host --pid host --userns host --cap-add audit_control \
    -e DOCKER_CONTENT_TRUST=1 \
    -v /etc:/etc:ro \
    -v /usr/lib/systemd:/usr/lib/systemd:ro \
    -v /var/lib:/var/lib:ro \
    -v /var/run/docker.sock:/var/run/docker.sock:ro \
    --label docker_bench_security \
    docker/docker-bench-security
```
