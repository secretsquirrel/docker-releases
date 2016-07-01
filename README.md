# docker-releases
DockerFIles for BDF/BDFProxy

## the-backdoor-factory
Usage:

```
docker pull secretsquirrel/the-backdoor-factory
docker run -it secretsquirrel/the-backdoor-factory bash
# ./backdoor.py
```

## bdfproxy
Usage:

```
 # sudo echo 1 > /proc/sys/net/ipv4/ip_forward  # linux
 # sudo sysctl -w net.inet.ip.forwarding=1 # macOS
 docker pull secretsquirrel/bdfproxy
 docker run -it -p 8080:8080 secretsquirrel/bdfproxy bash
 # ./bdf_proxy.py
```
