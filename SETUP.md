# Environment Setup Guide

## 🔒 Security Notice
**NEVER commit .env files to Git!** They contain sensitive information.

## Required Environment Variables

Create a `.env` file in the backend directory with these variables:

```bash
# Database Configuration
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=interview_assistant
DB_PORT=3306

# JWT Secret
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production

# Stripe Configuration (REQUIRED for payments)
STRIPE_SECRET_KEY=sk_test_your_stripe_secret_key_here
STRIPE_WEBHOOK_SECRET=whsec_your_webhook_secret_here

# CORS Origins (comma-separated)
CORS_ORIGINS=http://localhost:3000,https://yourdomain.com

# Server Port
PORT=5050
```

## How to Get Stripe Keys

1. Go to [Stripe Dashboard](https://dashboard.stripe.com/apikeys)
2. Copy your **Secret Key** (starts with `sk_test_` for test mode)
3. For webhook secret, go to [Webhooks](https://dashboard.stripe.com/webhooks) and create an endpoint

## Deployment Setup

### Railway
1. Go to your Railway project
2. Navigate to Variables tab
3. Add each environment variable from above

### Vercel
1. Go to your Vercel project
2. Navigate to Settings > Environment Variables
3. Add each environment variable

### Local Development
1. Copy `.env.example` to `.env`
2. Fill in your actual values
3. Restart your server

## Testing
After setting up, restart your backend server and test the payment endpoint:
```bash
curl -X POST http://localhost:5050/api/payment/create-checkout-session
``` 