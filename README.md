# cloud.moulard.org
Who to m'y personale cloud in aws


Who to secure my personnal data and optimise the cost.

## why

I have install a lot of rapsberry and self hosted server in mu house. That great but ahter short time this server is off. Any time for one different reason

internet, electrical, failure.... 

ok some of my data is realy important for me. Mainly the familly photo. 

dropbox, drive, mega is nice services but for large data thas to expensive for me. 

For my photo, I think, the best place is on my home hard disk with one copy on AWS S3 on deep archive mode. I have 400go in irlande I whill pay 5€ by year. 

In free tier on AWS is possible to have a small VM for free with 30go for 0€. 

That great for me. 

## who

I use 3 machines 
- aws data
- aws app
- self hosted raspbery py whith one HD

One my contexte I use 2 vm on AWS probably often only one is a good choice

### aws-app

crontab 
```
*/5 * * * * docker exec -u www-data nextcloud-nextcloud-1 php cron.php > /tmp/nextcloud-app-1phpcron.log 2> /tmp/nextcloud-app-1phpcron.err

```

fstab
```
ec2-user@cloud.moulard.org:/home/ec2-user/DD /home/dd/cloudmoulardorg  fuse.sshfs noauto,x-systemd.automount,_netdev,reconnect,identityfile=/home/ec2-user/.ssh/guillaume.moulard@orange.com4096.id_rsa,allow_other,default_permissions,uid=33,gid=33 0 0

pi@127.0.0.1:/media/pi/GMOULARD1TO3 /home/dd/DDISSY fuse.sshfs port=1306,x-systemd.automount,_netdev,reconnect,identityfile=/home/ec2-user/.ssh/guillaume@moulard.org.id_rsa,allow_other,default_permissions,uid=33,gid=33 0 0

```

### raspbarry pi


crontab 
```
@reboot /home/pi/pi-appliance/autossh.sh

```

Install docker
```
sudo apt-get update && sudo apt-get upgrade
.....

sudo usermod -aG docker pi
sudo usermod -aG docker ${USER}
sudo systemctl enable docker

```

un-Install docker
https://dev.to/elalemanyo/how-to-install-docker-and-docker-compose-on-raspberry-pi-1mo
```
sudo apt-get purge docker-ce
sudo apt-get purge docker-ce-cli
sudo rm -rf /var/lib/docker

```

