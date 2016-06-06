# docker-sinusbot
Debian Jessie with Sinusbot by Michael Friese.
TeamSpeak 3 SinusBot Homepage: https://frie.se/ts3bot/.

## Summary
* Debian Jessie with the latest version of Sinusbot
* You can inject your data into the container
  * /data
  
## Usage
### Permissions
The default UID of the user which is used in the container is 1000.
So if you mount a directory from your host you have to set the permission to the user with the UID of 1000, also commonly the first non-root user you added to your system.
Regardless make sure to set the correct permissions on your data directory with the following command:
```
chown -R 1000:1000 /data/sinusbot
```

### Mount host directory
```
docker run --name sinusbot -d -v /data/sinusbot:/sinusbot/data -p 8087:8087 samistine/sinusbot:latest
```

### Mount host directory - Beta Version
```
docker run --name sinusbot -d \
-v /data/sinusbot:/sinusbot/data \
-v /data/sinusbot/scripts:/sinusbot/scripts \
-p 8087:8087 samistine/sinusbot:latest
```

### SELinux
If your host uses SELinux it may be necessary to use the **:z** option:
```
docker run --name sinusbot -d -v /data/sinusbot:/sinusbot/data:z -p 8087:8087 samistine/sinusbot:latest
```