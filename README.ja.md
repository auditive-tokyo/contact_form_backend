# Contact Form Backend

[English](README.md)

Zoho Mailユーザー向けの、シンプルなコンタクトフォームバックエンドです。

## これは何？

Zoho MailのSMTPを使って、Webサイトのコンタクトフォームからメールを送信するシンプルなPythonコードです。

AWS Lambda、Cloud Functions、VPSなど、好きな環境で動かせます。

## コア部分

重要なのは [app.py](app.py) だけです。Zoho MailのSMTPでメールを送信するシンプルなコードなので、直接見てください。

## Zoho Mailの準備

1. 2段階認証を有効化
2. アプリパスワードを生成
   - Zoho Mail → 設定 → セキュリティ → アプリパスワード

## AWS SAMでデプロイする場合

SAMテンプレート付きなので、そのままデプロイできます：

```bash
sam build && sam deploy --guided
```

必要な環境変数：
- `SENDER_EMAIL` - 送信元メールアドレス
- `RECEIVER_EMAIL` - 受信先メールアドレス  
- `APP_PASSWORD` - Zohoのアプリパスワード

## API仕様

```
POST /
Content-Type: application/json

{
  "name": "名前",
  "email": "返信先メール",
  "message": "本文"
}
```

## フロントエンド例

```javascript
await fetch('YOUR_ENDPOINT_URL', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name, email, message })
});
```

## 他の環境で使いたい場合

Terraform、GCP、Vercel、自前サーバーなど、好きな環境に app.py のロジックを移植してください。

## ライセンス

MIT
