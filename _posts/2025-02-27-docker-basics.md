---
layout: post
title: "Dockerの基本：コンテナ技術入門"
date: 2025-02-27 14:00:00 +0900
categories: infrastructure
---

## Dockerとは

Dockerは、アプリケーションをコンテナと呼ばれる軽量な実行環境にパッケージ化し、どこでも同じように実行できるようにするプラットフォームです。コンテナは仮想マシンよりも軽量で、ホストOSのカーネルを共有しながら分離された環境を提供します。

## Dockerの主要コンポーネント

### 1. Dockerイメージ

Dockerイメージは、アプリケーションとその依存関係を含む読み取り専用のテンプレートです。イメージはDockerfileから作成されます。

```dockerfile
# Node.jsアプリケーションのDockerfile例
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### 2. Dockerコンテナ

コンテナはイメージの実行インスタンスです。同じイメージから複数のコンテナを作成できます。

### 3. Dockerレジストリ

DockerレジストリはDockerイメージを保存・共有するためのリポジトリです。Docker Hubは最も一般的なパブリックレジストリです。

## 基本的なDockerコマンド

### イメージの管理

```bash
# イメージのビルド
docker build -t myapp:1.0 .

# イメージの一覧表示
docker images

# イメージの削除
docker rmi myapp:1.0
```

### コンテナの管理

```bash
# コンテナの作成と起動
docker run -d -p 3000:3000 --name mycontainer myapp:1.0

# 実行中のコンテナの一覧表示
docker ps

# すべてのコンテナの一覧表示（停止中も含む）
docker ps -a

# コンテナの停止
docker stop mycontainer

# コンテナの削除
docker rm mycontainer
```

## Docker Composeによる複数コンテナの管理

Docker Composeを使用すると、複数のコンテナを定義し、一度に起動・停止できます。

```yaml
# docker-compose.yml
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
  db:
    image: mongo:4.4
    volumes:
      - mongo-data:/data/db
volumes:
  mongo-data:
```

基本的なDocker Composeコマンド：

```bash
# サービスの起動
docker-compose up -d

# サービスの停止
docker-compose down

# サービスの状態確認
docker-compose ps
```

## Dockerの利点

1. **一貫性のある環境**: 「自分のマシンでは動くのに」という問題を解消
2. **分離**: アプリケーション間の依存関係の競合を防止
3. **効率性**: 仮想マシンよりも軽量で高速
4. **スケーラビリティ**: 簡単に複製・スケールアップが可能
5. **バージョン管理**: イメージのバージョン管理が容易

## まとめ

Dockerはアプリケーションの開発、テスト、デプロイを効率化するための強力なツールです。コンテナ技術を活用することで、環境の一貫性を保ちながら、アプリケーションのライフサイクル全体を管理できます。
