# DVMHost in Containers

> [!WARNING] 
> This is very much a "proof-of-concept" at this time. Your mileage may vary.


# DVMHost Configs
You'll need a complete set of dvmhost configs in a folder: 
* iden_table.dat
* rid_acl.dat
* tg_acl.dat
* configCC.yml  (dvmhost config for your control channel)
* configVC.yml  (dvmhost config for your voice channel)

Clone the repo.

Set up a `.env` file in the cloned repo:
```
CONFIG_DIR=/opt/dvmhost/configs
CC_DEVICE=/dev/ttyAMA0
VC_DEVICE=/dev/ttyUSB0
```

Set CONFIG_DIR to the location of your config files, and set the devices to the appropriate dvm devices.

Then start it up:

```bash
docker compose up -d
```

To see logs,

```bash
docker compose logs -f
```

