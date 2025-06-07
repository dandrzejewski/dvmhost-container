# DVMHost in Containers

> [!WARNING] 
> This is very much a "proof-of-concept" at this time. Your mileage may vary.


After cloning the repo, build the container image:

```bash
cd dvmhost-docker
docker build -t dvmhost:latest .
cd ..
```

Make sure the `devices` sections are correct for your hardware, and make sure the volume mounts for the configs match your configs.

Then start it up:

```bash
docker compose up -d
```

To see logs,

```bash
docker compose logs -f
```


# Config Notes
In your dvmhost configs, you'll want to set:

```yaml
daemon: false
log:
  fileLevel: 0
  filePath: .
```

