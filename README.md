# Chatwork API Actions

GitHub Actionsワークフロー内でChatwork APIを簡単に扱うためのカスタムアクションセットです。様々なChatwork API操作を抽象化し、ワークフロー内での使用を容易にします。

## 主な機能

- メッセージの送信、取得
- ファイルのアップロード、管理
- タスクの作成、更新
- ルームの作成、管理、削除
- ユーザー情報の取得
- など、Chatwork APIの主要機能をカバー

## 基本的な使用方法

以下は基本的な使用例です。

```yaml
name: サンプルワークフロー

on:
  workflow_dispatch:

jobs:
  chatwork-api-sample:
    runs-on: ubuntu-latest
    steps:
      - name: メッセージ送信
        uses: kentanakae/chatwork-api-actions/send-message@v1
        with:
          api_token: ${{ secrets.CHATWORK_API_TOKEN }}
          room_id: "<ROOM_ID>"
          body: "GitHub Actionsからの通知です"
```

## 利用可能なアクション一覧

### 取得系

- `get-me`: 自分の情報を取得する
- `get-my-status`: 自分のステータスを取得する
- `get-my-tasks`: 自分のタスク一覧を取得する
- `get-contacts`: コンタクト一覧を取得する
- `get-incoming-requests`: コンタクト承認依頼一覧を取得する
- `get-rooms`: チャットルーム一覧を取得する
- `get-room`: チャットルーム情報を取得する
- `get-room-members`: チャットルームのメンバー一覧を取得する
- `get-room-messages`: チャットルームのメッセージ一覧を取得する
- `get-room-message`: 特定のメッセージ情報を取得する
- `get-room-tasks`: チャットルームのタスク一覧を取得する
- `get-room-task`: 特定のタスク情報を取得する
- `get-room-files`: チャットルームのファイル一覧を取得する
- `get-room-file`: 特定のファイル情報を取得する
- `get-room-link`: チャットルームの招待リンク情報を取得する

### 作成・更新系

- `send-message`: メッセージを送信する
- `create-room`: チャットルームを作成する
- `create-room-task`: チャットルームにタスクを作成する
- `update-room`: チャットルーム情報を更新する
- `update-room-members`: チャットルームのメンバーを更新する
- `update-room-task-status`: タスクのステータスを変更する
- `update-room-link`: チャットルームの招待リンクを作成・更新する
- `upload-room-file`: チャットルームにファイルをアップロードする

### その他

- `read-room-messages`: チャットルームのメッセージを既読にする
- `unread-room-message`: チャットルームのメッセージを未読にする
- `handle-incoming-request`: コンタクト承認依頼を承認・拒否する
- `delete-room`: チャットルームを削除（退室）する
- `delete-room-link`: チャットルームの招待リンクを削除する

## アクションの使用方法

各アクションは以下の形式で使用します:

```yaml
- name: アクション名
  uses: kentanakae/chatwork-api-actions/[アクション名]@v1
  with:
    api_token: ${{ secrets.CHATWORK_API_TOKEN }}
    # その他の必要なパラメータ
```

## セキュリティについて

### API トークンの取り扱い

Chatwork API トークンは機密情報です。以下のセキュリティのベストプラクティスを守ってください。

- API トークンは常にGitHub Secretsを使用して保存する
- トークンをログに出力したり、公開リポジトリにハードコードしない
- 必要最小限の権限を持つAPIトークンを使用する

### 認証情報の設定方法

以下の手順で認証情報をGitHub Secretsに設定してください。

1. リポジトリの Settings > Secrets > Actions を開く
2. `CHATWORK_API_TOKEN` という名前で、ChatworkのAPIトークンを保存する

詳細な手順は[GitHubの公式ドキュメント](https://docs.github.com/ja/actions/security-guides/encrypted-secrets)を参照してください。

## 注意事項

- このリポジトリは開発者の個人的な用途として作成されたものですが、誰でも自由に利用できます
- 定期的なメンテナンスを保証するものではなく、API仕様の変更に対応できない場合があります
- 重要なシステム連携には十分なテストの上でご利用ください
