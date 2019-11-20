## 1. Get the list of the network interfaces of the machine without displaying any detail for these interfaces. Only the list of names.
```
ifconfig -l
```

## 2.
### a) Identify broadcast address
```ifconfig en0 | awk '/inet /{print $6}'```
### b) Identify all IP adresses which are part of the same subnet
```
##	$> ifconfig en0 | awk '/inet /{print $6}'
##	10.113.255.255

ping -c 4 10.113.255.255 | grep "10.113."
```

## 3. Identify the MAC address of the Wi-Fi card
```
ifconfig en1 | awk '/ether/{print $2}'
```

## 4. Identifiy the default gateway in the routing table
```
netstat -nr | awk '/default/{print $2}' | head -1
```

## 5. Identify the IP address of the DNS that responds to the following url: slash16.org
```
nslookup slash16.org | awk '/Server:/{print $2}'
```

## 6. Get the complete path of the file that contains the IP address of the DNS server you're using
```
$> ls -l /etc/resolv.conf
lrwxr-xr-x  1 root  wheel    22 Nov  8  2017 /etc/resolv.conf -> ../var/run/resolv.conf
$> ls -l /var/run/resolv.conf
-rw-r--r--  1 root  daemon  374 Aug 28 09:24 /var/run/resolv.conf
```

## 7. Query an external DNS server on the slash16.org domain name (ie.: google 8.8.8.8)
```
nslookup slash16.org 8.8.8.8
```

## 8. Find the provider of slash16.org
```
$> whois slash16.org | awk '/Name Server:/{print $3}'
NS-1236.AWSDNS-26.ORG
NS-144.AWSDNS-18.COM
NS-686.AWSDNS-21.NET
NS-1989.AWSDNS-56.CO.UK
ns-144.awsdns-18.com
ns-1989.awsdns-56.co.uk
ns-1236.awsdns-26.org
ns-686.awsdns-21.net

$> nslookup slash16.org | sed -e '1,/^Non-authoritative answer/d' | awk '/Address:/{print $2}' | head -1
52.84.245.145
$> dig +short -x 52.84.245.145
server-52-84-245-145.sfo20.r.cloudfront.net.
```

## 9. Find the external IP of 42.fr
```
##	$> ping 42.fr -c 1 | awk -F '[()]' '{print $2}' | head -1

163.172.250.11
```

## 10. Identify the network devices between your computer and the slash16.org domain
```
traceroute slash16.org
```

## 11. Use the output of the previous command to find the name and IP address of the device that makes the link between you (local network) and the outside world
```
$> traceroute slash16.org
traceroute: Warning: slash16.org has multiple addresses; using 52.84.245.199
traceroute to slash16.org (52.84.245.199), 64 hops max, 52 byte packets
 1  10.113.254.254 (10.113.254.254)  0.943 ms  0.403 ms  0.350 ms
 2  192.168.0.2 (192.168.0.2)  0.602 ms  0.491 ms  0.342 ms
 3  nat (10.90.1.11)  0.226 ms  0.267 ms  0.219 ms
 4  64.62.224.30 (64.62.224.30)  0.799 ms  0.826 ms  0.814 ms
 5  64.62.224.253 (64.62.224.253)  3.647 ms  3.538 ms  3.506 ms
 6  64.62.224.249 (64.62.224.249)  3.812 ms  3.866 ms  3.837 ms
 7  v1851.core2.fmt2.he.net (216.218.200.77)  3.357 ms  3.299 ms  3.295 ms
 8  100ge10-1.core3.fmt2.he.net (72.52.92.29)  3.474 ms  3.599 ms  3.347 ms
 9  100ge9-1.core1.pao1.he.net (184.105.222.90)  4.058 ms
    100ge10-2.core1.pao1.he.net (184.105.222.6)  4.097 ms
    100ge9-1.core1.pao1.he.net (184.105.222.90)  4.205 ms
10  paix01-sfo4.amazon.com (198.32.176.36)  4.397 ms  4.219 ms  4.187 ms
11  54.240.243.108 (54.240.243.108)  5.160 ms  5.142 ms
    54.240.243.8 (54.240.243.8)  5.193 ms
12  54.240.243.117 (54.240.243.117)  4.606 ms
    54.240.243.15 (54.240.243.15)  4.621 ms
    54.240.243.159 (54.240.243.159)  4.457 ms
13  205.251.231.120 (205.251.231.120)  4.843 ms
    205.251.231.116 (205.251.231.116)  7.070 ms
    205.251.231.122 (205.251.231.122)  4.719 ms
14  * * *
15  * * *
16  * * *
17  server-52-84-245-199.sfo20.r.cloudfront.net (52.84.245.199)  4.707 ms  5.239 ms  4.577 ms
$> dig +short -x 10.90.1.11
nat.42.us.org.
```

## 12. Find the IP that was assigned to you by dhcp server
```
ifconfig en0 | awk '/inet /{print $2}'
```

## 13. Thanks to the previous question and the reverse DNS find the name of your host
```
##	$> ifconfig en0 | awk '/inet /{print $2}'
##	10.113.2.22
##	$> dig +short -x 10.113.2.22
##	e1z3r2p22.42.us.org.
##	$> nslookup 10.113.2.22 | awk '/name/{print $4}'
##	e1z3r2p22.42.us.org.

e1z3r2p22.42.us.org.
```

## 14. What file contains the local DNS entries?
```
$> ls -l /etc/ | grep "hosts"
-rw-r--r--   1 root  wheel     112 Apr 16  2018 hosts
-rw-r--r--   1 root  wheel       0 Oct  2  2017 hosts.equiv
$> cat /etc/hosts
127.0.0.1       localhost
255.255.255.255 broadcasthost
::1             localhost

#10.51.1.38 	cdn.intra.42.fr
```

## 15. Make the intra.42.fr address reroute to 46.19.122.85
```
Add a line in the format of [IP address] [url] to /etc/hosts
```
