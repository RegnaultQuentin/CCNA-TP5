<h1>Rendu Tp5</h1>


<h3>Tableau des adresses ip</h3>
<table>
  <tr>
    <td>Machine</td><td>net1</td><td>net2</td><td>net12</td>
  </tr>
  <tr>
    <td>client1</td><td>X</td><td>10.5.2.10</td><td>X</td>
  </tr>
  <tr>
  <td>client2</td><td>X</td><td>10.5.2.11</td><td>X</td>
  </tr>
  <tr>
    <td>routeur1</td><td>10.5.1.254</td><td>X</td><td>10.5.12.1</td>
  </tr>
  <tr>
    <td>routeur2</td><td>X</td><td>10.5.2.254</td><td>10.5.12.2</td> 
  </tr>
  <tr>
    <td>serveur1</td><td>10.5.1.10</td><td>X</td><td>X</td>
  </tr>
</table>
//mask 255.255.255.252"
<h2>IPs VMs</h2>
Ip seveur1
```
 inet 10.5.1.10/24 brd 10.5.1.255 scope global noprefixroute enp0s3

```
Fichier hots
```
route 10.5.2.0/24 via 10.5.1.254 dev enp0s3
hosts
10.5.2.10   client1 client1.tp5.b1
10.5.2.11   client2 client2.tp5.b1
```

Ip client1
```
 inet 10.5.2.10/24 brd 10.5.2.255 scope global noprefixroute enp0s3

```
Fichier hots 
```
route 10.5.1.0/24 via 10.5.2.254 dev enp0s3
hosts
10.5.2.11   client2 client2.tp5.b1
10.5.1.10   server1 serveur1.tp5.b1
```

Ip client2

```
 inet 10.5.2.11/24 brd 10.5.2.255 scope global noprefixroute enp0s3

```
Fichier hots
```
route 10.5.1.0/24 via 10.5.2.254 dev enp0s3
hosts
10.5.2.10   client1 client1.tp5.b1
10.5.1.10   server1 serveur1.tp5.b1
```
<h2>IPs Routeurs</h2>

Ip routeur1

```
router1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.5.1.254      YES NVRAM  up                    up
Ethernet0/1                10.5.12.1       YES NVRAM  up                    up
Ethernet0/2                unassigned      YES NVRAM  administratively down down
Ethernet0/3                unassigned      YES NVRAM  administratively down down
```

Ip routeur2
```
router2#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.5.12.2       YES NVRAM  up                    up
Ethernet0/1                10.5.2.254      YES NVRAM  up                    up
Ethernet0/2                unassigned      YES NVRAM  administratively down down
Ethernet0/3                unassigned      YES NVRAM  administratively down down

```

<h2>Ping</h2>
Ping client1 => serveur1 et retour
```
[root@client1 oui]$ ping server1
PING server1 (10.5.1.10) 56(84) bytes of data.
64 bytes from server1 (10.5.1.10): icmp_seq=1 ttl=62 time=33.5 ms

[root@client1 oui]$ ping client1
PING client1 (10.5.1.10) 56(84) bytes of data.
64 bytes from client1 (10.5.1.10): icmp_seq=1 ttl=62 time=28.7 ms
```

Ping client2 => serveur1 et retour
```
[root@client2 oui]$ ping server1
PING server1 (10.5.1.10) 56(84) bytes of data.
64 bytes from server1 (10.5.1.10): icmp_seq=1 ttl=62 time=31.6 ms

[root@client2 oui]$ ping client2
PING client2 (10.5.1.10) 56(84) bytes of data.
64 bytes from client2 (10.5.1.10): icmp_seq=1 ttl=62 time=29.8 ms
```