# uchiai-monorepo

このリポジトリは、Next.js（フロントエンド）と NestJS（バックエンド）を pnpm ワークスペースで統合したモノレポ構成のサンプルです。  
MVP 段階の開発・検証を迅速に開始できるテンプレートとして利用できます。

## 概要

- **パッケージマネージャ**: pnpm
- **フロントエンド**: Next.js (React + TypeScript)
- **バックエンド**: NestJS (Node.js + TypeScript)



## 前提条件

- **Node.js**: v18 以上を推奨（pnpm が Node.js 18.12 以上を要求）
- **pnpm**: インストールされていない場合は以下のコマンドで導入
```bash
npm install -g pnpm

corepack enable
corepack prepare pnpm@latest --activate
```

## セットアップ手順

1. リポジトリをクローン
```bash
git clone https://github.com/your-username/uchiai-monorepo.git
cd uchiai-monorepo
```

2. 依存パッケージのインストール
```bash
pnpm install
```
これにより、apps/frontend、apps/backend、packages/shared すべての依存関係がインストールされます。

3. 開発サーバーの起動
```bash
pnpm dev
```
* pnpm dev:backend が apps/backend で NestJS の開発サーバ（デフォルトで http://localhost:3000）を起動
* pnpm dev:frontend が apps/frontend で Next.js の開発サーバを起動（ポート競合時には http://localhost:3001 など別ポートで起動）
* ブラウザで http://localhost:3001 にアクセスすると、Next.js フロントエンドが表示されます。
* バックエンド API は http://localhost:3000/api（NestJS 側の設定により異なる）を通してアクセス可能です。

## ビルド＆本番起動（任意）
* バックエンドビルド
``` bash
pnpm build:backend
```

* フロントエンドビルド
``` bash
pnpm build:frontend
```

## 環境変数
.env、.env.local などのファイルは .gitignore により無視されます。必要な環境変数はプロジェクトルートまたは各 apps ディレクトリ内で .env ファイルを用意して設定してください。

## 今後の拡張
- 認証・認可（Auth0、JWT など）の追加
- DB 接続・マイグレーション（Prisma や TypeORM）
- CI/CD パイプライン整備（GitHub Actions, CircleCI など）
- ESLint, Prettier 導入によるコード整形
