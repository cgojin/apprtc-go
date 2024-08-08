# apprtc-go

apprtc demo with golang. It's rewrite the project WebRTC [apprtc](https://github.com/webrtc/apprtc) with golang.

## Install apprtc-go and run

```sh
go get github.com/daozhao/apprtc-go
cd $GOPATH/src/github.com/daozhao/apprtc-go/
go build apprtc.go

./apprtc --help
  Usage of ./apprtc:
    -cert string
          cert pem file  (default "./mycert.pem")
    -httpport int
          The http port that the server listens on (default 8080)
    -httpsport int
          The https port that the server listens on (default 8888)
    -key string
          cert key file  (default "./mycert.key")
    -room-server string
          The origin of the room server (default "https://appr.tc")
    -stun string
          Enter stun server ip:port,for example 192.168.2.170:3478,default is null
    -turn string
          Enter turn server ip:port,for example 192.168.2.170:3478,default is null
    -turn-password string
          Enter turn server user password,default is null
    -turn-static-auth-secret string
          Enter turn server static auth secret,default is null
    -turn-username string
          Enter turn server username,default is null

./apprtc
```

Open chrome and enter URL(https://192.168.2.170:8888 or https://192.168.2.170:8080 ).

warnning: Replace the IP(192.168.2.170) with your real IP address.

## coturn

coturn[https://github.com/coturn/coturn]

### stun only

```sh
turnserver --no-auth --stun-only -v

./apprtc -stun=192.168.2.170:3478 
```

### turn with static username and password

```sh
turnserver -v  --user=daozhao:12345 --realm apprtc  --no-stun

./apprtc -turn=192.168.2.170:3478 -turn-username=daozhao -turn-password=12345 
```

### turn with auth-secret

```sh
turnserver -v --user=daozhao --realm apprtc --static-auth-secret=654321 --no-stun

./apprtc -turn=192.168.2.170:3478 -turn-username=daozhao -turn-static-auth-secret=654321
```

## Related project

apprtc-electron[https://github.com/daozhao/apprtc-electron]

