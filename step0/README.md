# Dockerfileとは？

dockerコンテナの設計図みたいなもの

Dockerfileをベースにしてdocker imageを作成し、imageを元にdocker containerを作成する


## Dockerfileの主な書式

### FROM

imageのベースとなるimage名を指定する

Dockerhubなどから探す

https://hub.docker.com/

```Dockerfile
FROM httpd
```

バージョンを指定することもできる

指定なしだとlatest扱いになるため、実行タイミングによってimageの中身がかわってしまうので指定するのがおすすめ

```Dockerfile
FROM httpd:2.4
```


### ENV 

image内の環境変数を設定/変更できる

```Dockerfile
ENV TZ Asia/Tokyo
```


### COPY/ADD

どちらも指定したファイルやフォルダをimage内に配置するためのコマンド

```Dockerfile
COPY ./file /home/hoge/
ADD ./file /home/hoge/
```

色々と細かい違いがあるが、主な違いは以下２つ

* ADD は コピー元にurlを指定できる
* ADD は コピー元が対応している圧縮ファイルだった場合、image内に解凍した状態で配置する
    * gzip、bzip2、xz 


### RUN

image内で実行するコマンドを指定する

```Dockerfile
RUN ls -l
```

単純にコマンドを記述する以外に、実行シェルも指定することができる

```Dockerfile
RUN ["/bin/zsh", "ls", "-l"]
```



