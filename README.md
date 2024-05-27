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

# 4. Check again
ip route show
# default via 172.20.74.1 dev enx7cc2c6468386 metric 101
# default via 192.168.0.254 dev eno1 proto static metric 102
# ...
```
