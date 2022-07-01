# unbound
This repository contains docker-compose files for adding an unbound container on either a Synology NAS or Raspberri Pi that is already running a docker instance of Pi-Hole setup with Network: Host option.

I already had a docker instance of Pi-Hole running in a container on both my Raspberry Pi (Primary) and Synology NAS (Secondary).

Both Pi-Hole instances were running flawlessly but I wanted the extra privacy afforded by unbound. I tried multiple methods, bridge networking, macvlans, single images with both, but none worked or could be simply spun up on either hardware without major changes.

So by trial and error I was able to get unbound to work with the docker-compose examples in this repository.

Here's how to proceed:
1. In the path of your choice, create a folder called unbound.
2. Copy the files (a-records.conf, forward-records.conf, srv-records.conf) provided in this repository to that folder. For some reason a fatal error occurs in unbound when they do not exist and it never fully starts. You can create empty files with those names as well, the ones in this repository are completely empty.
3. Run docker-compose with your method of choice, making sure you change the mount point to wherever you created your unbound foler. I used Portainer.
4. Once the container is up and running, go to your Pi-Hole's control panel and add the Host's IP adress followed by #8053 (if you used the same ports as I did) in custom upstream #1.
5. Uncheck all other DNS, save.
![plot](https://github.com/snaky69/unbound/blob/main/images/DNS%20Setup.png)
6. In settings, restart DNS. (not sure if this is needed but I did it for good measure)
![plot](https://github.com/snaky69/unbound/blob/main/images/Restart%20DNS.png)
