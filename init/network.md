## 1. Get the list of the network interfaces of the machine without displaying any detail for these interfaces. Only the list of names.
```ifconfig -l```

## 2.
### a) Identify broadcast address
```ifconfig en0 | awk '/inet /{print $6}'```
### b) Identify all IP adresses which are part of the same subnet
```
##	$> ifconfig en0 | awk '/inet /{print $6}'
##	10.113.255.255

ping -c 4 10.113.255.255 | grep "10.113."
```
