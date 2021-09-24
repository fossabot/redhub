<p align="center">
<img 
    src="https://user-images.githubusercontent.com/12872991/134626503-c022bb8e-2d5c-4760-a470-f56ff8ef036f.png" 
    border="0" alt="REDHUB">
<br>


Features
--------
- Create a Redis compatible server with RawEpoll model in Go

Installing
----------

```
go get -u github.com/IceFireDB/redhub
```

Example
-------

Here's a full example of a Redis clone that accepts:

- SET key value
- GET key
- DEL key
- PING
- QUIT

You can run this example from a terminal:

```sh
go run example/server.go
```

Benchmarks
----------

```
# Machine information
        OS : CentOS Linux release 7.9.2009 (Core)
       CPU : 4 CPU cores
    Memory : 32.0 GiB

# Go version
Go Version : go1.16.5 linux/amd64

```

**Redis-server**: no disk persistence

```
$ ./redis-server --port 6379 --appendonly no
```
```
$ redis-benchmark -p 6379 -t set,get -n 10000000 -q -P 1024 -c 512
SET: 1864975.75 requests per second
GET: 2443792.75 requests per second
```
**Redhub**: no disk persistence

```
$ go run example/server.go
```
```
$ redis-benchmark -p 6380 -t set,get -n 10000000 -q -P 1024 -c 512
SET: 3033060.50 requests per second
GET: 6169031.50 requests per second
```
![dataset-simple0](https://user-images.githubusercontent.com/12872991/134624309-54d5f64d-4f8d-433a-8642-4bc2724b6dc7.png)

<!--
```
$ redis-benchmark -p 6380 -t set,get -n 10000000 -q -P 512 -c 512
SET: 2840909.00 requests per second
GET: 5643341.00 requests per second
```
-->


License
-------
Redhub source code is available under the Apache 2.0 [License](/LICENSE).
