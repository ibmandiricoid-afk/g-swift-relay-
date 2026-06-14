# G-Swift Relay

A fast email relay server built with Netlify Functions for sending emails through Bank Mandiri branding.

## Features

- ⚡ Fast email delivery using Node Mailer
- 🔒 SMTP authentication support
- 🎨 Bank Mandiri branded emails
- 📱 Modern React frontend
- 🚀 Netlify deployment ready

## Project Structure

```
g-swift-relay/
├── netlify/
│   └── functions/
│       ├── health.js       # Health check endpoint
│       └── send-email.js   # Email sending function
├── src/
│   ├── App.jsx            # Main React component
│   ├── main.jsx           # React entry point
│   └── index.css          # Global styles
├── index.html             # HTML template
├── netlify.toml           # Netlify configuration
├── package.json           # Dependencies
└── vite.config.js         # Vite configuration
```

## Setup

### Prerequisites

- Node.js 16+
- npm or yarn

### Installation

```bash
npm install
```

### Configuration

Create a `.env` file in the root directory:

```env
VITE_API_URL=http://localhost:8888
```

## Development

```bash
# Start local development server
npm run dev

# Run with Netlify functions
netlify dev
```

## Deployment

### Deploy to Netlify

1. Connect your repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`

Or use Netlify CLI:

```bash
netlify deploy --prod
```

## API Endpoints

### Health Check

```http
GET /api/health
```

Response:
```json
{
  "status": "ok",
  "relay": "active",
  "message": "G-Swift Relay active. System ready.",
  "timestamp": "2024-01-10T12:00:00.000Z"
}
```

### Send Email

```http
POST /api/send-email
Content-Type: application/json

{
  "to": "recipient@example.com",
  "subject": "Email Subject",
  "html": "<p>HTML content</p>",
  "text": "Plain text content",
  "smtp": {
    "host": "smtp.gmail.com",
    "port": 587,
    "user": "your-email@gmail.com",
    "pass": "your-app-password"
  }
}
```

Response:
```json
{
  "success": true,
  "message": "Email berhasil dikirim sebagai Bank Mandiri"
}
```

## Error Handling

- 400: Missing SMTP configuration
- 500: Email sending failed
- CORS enabled for cross-origin requests

## License

MIT
