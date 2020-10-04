# loadbalancer-in-go

Building a loadbalancer from scratch. DO NOT use this in production :P (just in case)

This repo accompanies a 2 part video series on YouTube:

- Part 1: [Building a LoadBalancer in Go](https://youtu.be/4i7_5NE6tlM)
- Part 2: [Building Health Check functionality for a LoadBalancer](https://youtu.be/r9mcmZEhD9Q)

## Running it

Start multiple instances of `server.py`

```bash
# create a virtual env (optional)
virtualenv env
source env/bin/activate

# install flask
pip install flask

# spawn multiple servers
for i in {1..5}; do python server.py "server-$i" "500$i" &; done
```

Start the loadbalancer

```bash
go run loadbalancer.go
```

Bombard the loadbalancer with requests

```bash
for i in {1..20}; do curl 127.0.0.1:8000; done
```

To kill all the instances of the servers

```bash
pkill -9 python
```
