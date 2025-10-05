# Deployment Guide

## Environment Variables

For Vercel deployment, you need to add the News API key as an environment variable:

1. Go to your Vercel project settings
2. Navigate to "Environment Variables"
3. Add: `REACT_APP_NEWS_API` with your API key value: `88e9d0a59a894d6b9cbb3235c6fcd083`
4. Make sure to add it for all environments (Production, Preview, Development)

## Important Notes

### HTTP 426 Error (Upgrade Required)

The News API free tier has limitations:
- **CORS restrictions**: The free tier may not work from browser-based applications deployed on domains
- **HTTPS requirement**: Some endpoints require HTTPS
- **Rate limits**: 100 requests per day for developer accounts

### Solutions:

1. **Use a proxy server**: Create a backend API that fetches from News API and serves to your frontend
2. **Upgrade News API plan**: Consider upgrading to a paid plan that supports CORS
3. **Alternative approach**: Use a different news API that supports free tier CORS

### Current Fix Applied

The code now handles API errors gracefully:
- Won't crash if `articles` is undefined
- Shows empty state instead of breaking
- Logs errors to console for debugging

## Testing Locally

```bash
# Make sure .env file exists with your API key
echo "REACT_APP_NEWS_API=your_api_key_here" > .env

# Install dependencies
npm install

# Start development server
npm start
```

## Vercel Deployment

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Add environment variable via CLI
vercel env add REACT_APP_NEWS_API
```
