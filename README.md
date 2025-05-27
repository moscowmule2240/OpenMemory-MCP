# OpenMemory MCP

OpenMemory MCPは、Mem0を使用したメモリ管理システムです。Dockerコンテナとして構成されており、Qdrantベクトルデータベースを使用してメモリを永続化します。

## 構成

このプロジェクトは以下のサービスで構成されています：

- **mem0_store**: Qdrantベクトルデータベース（ポート6333）
- **openmemory-mcp**: OpenMemory MCPサーバー（ポート8765）
- **openmemory-ui**: WebUI（ポート3000）

## 起動方法

### 前提条件

- Docker
- Docker Compose
- PowerShell（Windows）または PowerShell Core（macOS/Linux）

### 起動

プロジェクトを起動するには、以下のコマンドを実行してください：

```powershell
./start.ps1
```

または、直接Docker Composeを使用する場合：

```bash
docker compose up -d
```

### アクセス

起動後、以下のURLでサービスにアクセスできます：

- **Web UI**: http://localhost:3000
- **MCP Server**: http://localhost:8765
- **Qdrant**: http://localhost:6333

### 停止

サービスを停止するには：

```bash
docker compose down
```

## 環境設定

プロジェクトルートに`.env`ファイルを作成し、必要な環境変数を設定してください。

## トラブルシューティング

### ポートが使用中の場合

他のサービスが同じポートを使用している場合は、`docker-compose.yml`のポート設定を変更してください。

### データの永続化

Qdrantのデータは`mem0_storage`という名前のDockerボリュームに保存されます。データを完全に削除したい場合は：

```bash
docker compose down -v
```
