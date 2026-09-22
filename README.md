# TaskNote (Laravel x React Kanban App)

PHPとSPA（Single Page Application）構成の学習を目的として作成した、カンバン方式のタスク管理アプリケーションです。
フロントエンドとバックエンドを完全に分離し、Docker環境で構築しています。

## 🛠 技術スタック

### Frontend
- React 19
- TypeScript 7.x
- Vite
- Tailwind CSS v4

### Backend
- PHP 8.x
- Laravel 13.x
- MySQL 8.x

### Infrastructure
- Docker / Docker Compose
- Nginx

## 📁 ディレクトリ構成

```text
.
├── backend/       # Laravel APIサーバー
├── frontend/      # React (Vite) クライアント
├── docker/        # Dockerコンテナ用の設定ファイル（Nginx, PHP, postgreSQL）
├── docker-compose.yml
└── README.md
```

## 🚀 環境構築手順 (Getting Started)

前提条件: Docker および Docker Compose がインストールされていること。

1. **リポジトリのクローン**
   ```bash
   git clone https://github.com/your-username/laravel-react-kanban.git
   cd laravel-react-kanba
   ```

2. **Dockerコンテナの起動**
   ```bash
   docker compose up -d
   ```

3. **バックエンド (Laravel) のセットアップ**
   ```bash
   # PHPコンテナに入りパッケージをインストール
   docker compose exec app composer install
   
   # 環境変数の設定とキー生成
   docker compose exec app cp .env.example .env
   docker compose exec app php artisan key:generate
   
   # データベースのマイグレーション
   docker compose exec app php artisan migrate
   ```

4. **フロントエンド (React) のセットアップ**
   ```bash
   # Nodeコンテナに入りパッケージをインストール
   docker compose exec web npm install
   
   # 開発サーバーの起動
   docker compose exec web npm run dev
   ```

5. **ブラウザで確認**
   - Frontend: `http://localhost:5173`
   - Backend API: `http://localhost:8000/api`

## ✨ 主な機能

- ボード、カラム、タスクの作成・編集・削除
- ドラッグ＆ドロップによるタスクの並び替え・移動（同じカラム内 / 別カラム間）
- API通信を通じたリアルタイムな状態管理
