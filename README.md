# 使い方

## 環境構築

### 1. インストール用コンテナ立ち上げ ＆ Next.js インストール

```
$ docker-compose -f docker-compose.install.yml up -d
```

### 2. Storybook インストール

```
$ docker-compose exec app pnpm dlx storybook@latest init
```

※ インストール完了後にローカルサーバーを立ち上げようとして止まるので Ctrl + C で終了させる ( `[webpack-dev-middleware] wait until bundle finished` というメッセージで止まる)

### 3. ホストにコピー

一旦コンテナからログアウトして下記を実行。

```
$ docker cp node_app:/var/www/ ./myapp/
```

### 4. 開発用コンテナを立ち上げ

```
$ docker-compose up -d
```

### 5. コンテナに入る

```
$ docker-compose exec app bash
```

## 起動

### 1. コンテナのビルド＆起動

```
$ docker-compose up -d
```

### 2. コンテナに入る

```
$ docker-compose exec php bash
```

### 5. サイトにアクセスする

[サイト]
http://localhost:3000/

[Storybook]
http://localhost:6006/

[PhpMyAdmin]
http://localhost:8080/

[mailhog]
http://localhost:8025/

## 環境構築後

### コンテナを起動する

```
$ docker-compose up -d
```

### コンテナを停止する

```
$ docker-compose down
```

### コンテナを停止＆イメージ削除

```
$ docker-compose down --rmi all --volumes
```
