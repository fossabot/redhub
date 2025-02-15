<!--
 * @Author: gitsrc
 * @Date: 2021-09-24 15:07:31
 * @LastEditors: gitsrc
 * @LastEditTime: 2021-09-24 15:37:51
 * @FilePath: /redhub/docs/index.md
-->

<p align="center">
    <img 
        src="https://user-images.githubusercontent.com/12872991/134626503-c022bb8e-2d5c-4760-a470-f56ff8ef036f.png" 
        border="0" alt="REDHUB">
    <br>
    <a href="https://pkg.go.dev/github.com/IceFireDB/redhub"><img src="https://img.shields.io/badge/api-reference-blue.svg?style=flat-square" alt="GoDoc"></a>
</p>


# RedHub
High-performance Redis-Server framework, based on rawepoll model.
* high performance
* Compatible with redis protocol
* Create a Redis compatible server with RawEpoll model in Go

# Installing

```
go get -u github.com/IceFireDB/redhub
```

# Example

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

# Benchmarks

```
Machine information
        OS : CentOS Linux release 7.9.2009 (Core)
       CPU : 4 CPU cores
    Memory : 32.0 GiB

Go Version : go1.16.5 linux/amd64

```

## Redis-server5.0.3: no disk persistence

```
$ ./redis-server --port 6379 --appendonly no
```
```
$ redis-benchmark -p 6379 -t set,get -n 10000000 -q -P 1024 -c 512
SET: 1864975.75 requests per second
GET: 2443792.75 requests per second
```

## Redis-server6.2.5: no disk persistence

```
$ ./redis-server --port 6379 --appendonly no
```
```
$ redis-benchmark -p 6379 -t set,get -n 10000000 -q -P 1024 -c 512
SET: 1690617.12 requests per second
GET: 2201188.50 requests per second
```
## Redhub: no disk persistence

```
$ go run example/server.go
```
```
$ redis-benchmark -p 6380 -t set,get -n 10000000 -q -P 1024 -c 512
SET: 3033060.50 requests per second
GET: 6169031.50 requests per second
```



<p align="center">
    <img 
    src="https://user-images.githubusercontent.com/12872991/134629662-1d789503-ddab-4efd-a6b4-5620b5a9e8db.png" 
    border="0" alt="REDHUB Benchmarks">
    <br>
</p>


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


## Disclaimers
When you use this software, you have agreed and stated that the author, maintainer and contributor of this software are not responsible for any risks, costs or problems you encounter. If you find a software defect or BUG, ​​please submit a patch to help improve it!
