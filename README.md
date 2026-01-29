# Contact Form Backend

[日本語](README.ja.md)

A simple contact form backend for Zoho Mail users.

## What is this?

Simple Python code to send emails from your website's contact form using Zoho Mail SMTP.

Works on AWS Lambda, Cloud Functions, VPS, or any environment you prefer.

## Core

All you need is [app.py](app.py). It's simple code that sends emails via Zoho Mail SMTP—just take a look.

## Zoho Mail Setup

1. Enable 2-factor authentication
2. Generate an app password
   - Zoho Mail → Settings → Security → App Passwords

## Deploy with AWS SAM

SAM template included. Just run:

```bash
sam build && sam deploy --guided
```

Required environment variables:
- `SENDER_EMAIL` - Sender email address
- `RECEIVER_EMAIL` - Receiver email address
- `APP_PASSWORD` - Zoho app password

## API

```
POST /
Content-Type: application/json

{
  "name": "Name",
  "email": "Reply-to email",
  "message": "Message body"
}
```

## Frontend Example

```javascript
await fetch('YOUR_ENDPOINT_URL', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name, email, message })
});
```

## Other Environments

Feel free to port the app.py logic to Terraform, GCP, Vercel, your own server, etc.

## License

MIT
