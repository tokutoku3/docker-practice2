# webサーバを立ててみる

## Dokerfileを元にapacheコンテナのimage作成

image作成

```
$ docker build -t vam/dp1 .
```

dp1が追加されてるはず

```
$ docker images
REPOSITORY                         TAG                                        IMAGE ID            CREATED             SIZE
vam/dp1                            latest                                     d1cafe366c3d        11 seconds ago      177MB

docker ps
#=> imageを作成しただけなのでコンテナは起動してないはず
```

## imageを元にコンテナを起動

先ほど作成したdp1イメージをベースにコンテナを起動する

```
$ docker run -dit -p 18080:80 --name my-dp1-1 vam/dp1
```

http://localhost:18080/ にアクセスできるようになったはず

また、起動中のコンテナにmy-dp1-1が追加されているはず

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND              CREATED                  STATUS              PORTS                   NAMES
01bfa228e871        vam/dp1             "httpd-foreground"   Less than a second ago   Up 3 seconds        0.0.0.0:18080->80/tcp   my-dp1-1
```

## ポートの設定などを変えれば複数のコンテナを起動できる

```
$ docker run -dit -p 18081:80 --name my-dp1-2 dp1
```