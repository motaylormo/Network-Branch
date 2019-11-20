## 1. In what file can you find the installed version of your Debian?
```
$> cat /etc/debian_version
10.0
```

## 2. What command can you use to rename your system?
```
sudo hostnamectl set-hostname [name]
```

## 3. What file has to be modified to make it permanent?
```
/etc/hostname
```

## 4. What command gives you the time since your system was last booted?
```
uptime
```

## 5. Name the command that determines the state of the SSH service.
```
systemctl status sshd
```

## 6. Name the command that reboots the SSH service.
```
sudo systemctl restart sshd
```

## 7. Figure out the PID of the SSHD service.
```
systemctl status sshd | awk '/PID/{print $3}'
```

## 8. What file contains the RSA keys of systems that are authorized to connect via SSH?
```
/etc/ssh/ssh_host_rsa_key
```

## 9. What command lets you know who is connected to the System?
```
who
```

## 10. Name the command that lists the partition tables of drives?
```
sudo fdisk -l
```

## 11. Name the command that displays the available space left and used on the system in an humanly understandable way
```
df -h
```

## 12. Figure out the exact size of each folder of `/var` in a humanly understandable way followed by the path of it.
```
du -s -h /var/*
```

## 13. Name the command that find, in real time, currently running processes
```
ps -aux
```

## 14. Run the `tail -f /var/log/syslog` command in background
```
sudo tail -f /var/log/syslog &
```

## 15. Find the command that kills the background command’s process
```
kill -$(pgrep tail)
```

## 16. Find the service which makes it possible to run specific tasks following a regular schedule
```
$> man cron
cron - daemon to execute scheduled commands (VixieCron)
```

## 17. Find the command that allows you to connect via ssh on the VM. (In parallel with the graphic session)
```
ssh -p 2200 motaylor@localhost
```

## 18. Find the command that kills ssh service
```
sudo kill $(pgrep sshd)
```

## 19. List all services which are started at boot time and name this kind of services
```
systemctl status
```

## 20. List all existing users on the VM
```
awk -F':' '{ print $1}' /etc/passwd
```

## 21. List all real users on the VM
```
awk -F':' '/home/{print $1}' /etc/passwd
```

## 22. Find the command that add a new local user
```
useradd
```

## 23. Explain how connect yourself as new user. (With graphic session and ssh session)
```
command su (switch user)
```

## 24. Find the command that list all packages
```
dpkg -l
```
