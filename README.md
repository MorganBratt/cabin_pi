# Notes
https://www.youtube.com/watch?v=lSwDGTg7Bqs

## configure the PI

Run the following command to change the default boot target to multi-user.target, which corresponds to the command-line mode:
``` sh
sudo systemctl set-default multi-user.target
```
Reboot
```
sudo reboot
```

## Optional install XRP
```sh
# Install XRDP and other necessary software
sudo apt update
sudo apt install -y xrdp
sudo systemctl enable xrdp
sudo systemctl start xrdp
```

## config the pi from the command line
```sh
sudo raspi-config
```

## docker container
https://docs.docker.com/engine/install/debian/

https://docs.linuxserver.io/images/docker-unifi-network-application/

https://github.com/jacobalberty/unifi-docker

```sh
docker run -d --init \
   --restart=unless-stopped \
   -p 8080:8080 -p 8443:8443 -p 3478:3478/udp \
   -e TZ='America/Los_Angeles' \
   -v ~/unifi:/unifi \
   --user unifi \
   --name unifi \
   jacobalberty/unifi
```

go to https://docker-host-address:8443  to finish 