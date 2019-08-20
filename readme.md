# 说明

模仿系统发送syn 包。
修改下代码，调整扫描目标
```go
ipstr := "172.17.0.2"
ports := []layers.TCPPort{10, 20, 30, 40} 
```

### tcp options
```go
layers.TCPOption{layers.TCPOptionKindMSS, 4,[]byte("\x05\xb4")},
layers.TCPOption{layers.TCPOptionKindSACKPermitted, 2, nil},
layers.TCPOption{layers.TCPOptionKindNop, 1, nil},
layers.TCPOption{layers.TCPOptionKindWindowScale, 3, []byte("\x07")},
```


### gopcaket route 包的问题

- out of order iface error
由于云主机里的有个网卡 vethdba2c Index 不是顺序递增了，导致出现错误。
- 未考虑默认路由，

`go get https://github.com/google/gopacket`  后修改相关代码  `routing/routing.go`
> https://github.com/jax777/gopacket/blob/master/routing/routing.go
>