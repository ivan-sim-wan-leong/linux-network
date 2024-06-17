# Linux Network

Just some notes about Linux networking.

## Temporary Changing IP Route Metric

```bash
# 1. Obtain available route
ip route show
# default via 192.168.0.254 dev eno1 proto static metric 102
# default via 172.20.74.1 dev enx7cc2c6468386 metric 103
# ...

# 2. Delete the route that you want to update the metric
sudo ip route del default via 172.20.74.1

# 3. Add the route back with the updated metric
sudo ip route add default via 172.20.74.1 metric 101
# or add without a metric if `RTNETLINK answers: File exists`
sudo ip route add default via 172.20.74.1

# 4. Check again
ip route show
# default via 172.20.74.1 dev enx7cc2c6468386 metric 101
# default via 192.168.0.254 dev eno1 proto static metric 102
# ...
```

Ref: https://unix.stackexchange.com/questions/245208/modifying-existing-route-entry-in-linux

## Query DNS Servers

```bash
dig redhat.com
# Just answer
dig redhat.com +noall +answer
# For mail exchange record
dig redhat.com MX +noall +answer
# For name server
dig redhat.com NX +noall +answer
# For all records
dig redhat.com ANY +noall +answer
# For shell script
dig redhat.com +short
# Reverse your query (ip -> server name)
dig -x 52.200.142.250 +short
```
