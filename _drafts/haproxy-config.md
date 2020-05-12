---
title: haproxy configuration
---

/etc/haproxy/haproxy.cfg

## global

```
global
```
<br/>

## defaults
```
```
<br/>

## frontend and backend
---
### None TLS
```
frontend http-in
    bind [ip]:80
    use_backend abc-servers if { path_beg /abc/ }
    use_backend xyz-servers if { path_beg /xyz/ }
    default_backend default-server

backend abc-servers
    balance roundrobin
    server server1 [abc server1 ip]:[port] maxconn [num]
    server server2 [abc server2 ip]:[port] maxconn [num]

backend xyz-servers
    balance roundrobin
    server server1 [xyz server1 ip]:[port] maxconn [num]
    server server2 [xyz server2 ip]:[port] maxconn [num]
```
<br/>

### TLS
``` 
frontend https-in
    bind {ip}:443 ssl crt [pem file path]
    use_backend https-server

backend https-server
    balance roundrobin
    server server1 [https server1 ip]:[port] ssl ca-file [ ca chain ] # or use "ssl verify none"

backend default-server
    server server1 {default server ip}:{port}

```
<br/>

## listen
```
```

### Tip!
``` bash
haproxy -c -f haproxy.cfg
```