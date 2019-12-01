# docker-compose によるローカル環境構築

## 環境構築
### 1. `cakephp3-template`ディレクトリに移動

```bash
$ cd cakephp3-template
```

### 2. .envファイル作成
```bash
$ cp .env.example .env
```

### 3. ビルド

```bash
$ docker-compose build
```

### 4. 起動（バックグラウンド）

```bash
$ docker-compose up -d
```

### 5. composer実行&データベース作成

```bash
$ docker-compose exec php bash
```

```bash
$ composer install
```
マイグレーション実行
```bash
$ bin/cake migrations migrate
```
seed反映
```bash
$ bin/cake migrations seed
```

```bash
# exit
```

## 動作確認

```bash
$ open localhost:8080
```

## コンテナ停止
```bash
$ docker-compose stop
```

## コンテナ削除
```bash
$ docker-compose rm
```
