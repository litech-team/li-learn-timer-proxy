# li-lern-timer-proxy

li-LernTimerのProxyサーバーのリポジトリです。

## サーバーの操作

### 起動
```sh
$ docker compose up -d nginx
```

### 停止
```sh
$ docker compose down
```


## サーバ証明書

### 取得
メールアドレスを書き換えて実行します。
```sh
$ docker compose run --rm certbot certonly \
    --manual \
    --preferred-challenges=dns \
    -d li-tech.net \
    -m <メールアドレス>
```

あとは指示通りにDNSの設定を行なっていきます。  
参考：https://qiita.com/AkiQ/items/db4eb8c7106f109819f0


### 更新
```sh
$ docker compose run --rm certbot renew
$ docker compose exec -T nginx nginx -s reload
```


## 参考サイト
- https://paulownia.hatenablog.com/entry/2020/09/12/150658
- https://kappaseijin.hatenablog.com/entry/2020/10/30/173056
- https://qiita.com/F_clef/items/136d81223c030904523c