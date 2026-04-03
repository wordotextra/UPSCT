# Deployment Guide for UPSCT

This guide covers deploying UPSCT to various platforms.

## Prerequisites
- Deployed application URL
- Environment variables configured
- Database setup (if applicable)

## Heroku Deployment

### 1. Install Heroku CLI
```bash
curl https://cli-assets.heroku.com/install.sh | sh
```

### 2. Login to Heroku
```bash
heroku login
```

### 3. Create Heroku App
```bash
heroku create your-app-name
```

### 4. Add Config Variables
```bash
heroku config:set FLASK_ENV=production
heroku config:set SECRET_KEY=your-secure-key
```

### 5. Deploy
```bash
git push heroku main
```

### 6. View Logs
```bash
heroku logs --tail
```

## AWS Elastic Beanstalk

### 1. Install AWS CLI & EB CLI
```bash
pip install awsebcli
```

### 2. Initialize EB Project
```bash
eb init -p "Python 3.11" --region us-east-1
```

### 3. Create Environment
```bash
eb create production-env
```

### 4. Deploy
```bash
eb deploy
```

## DigitalOcean App Platform

### 1. Push Code to GitHub
```bash
git push origin main
```

### 2. Connect on DigitalOcean
- Go to App Platform
- Connect GitHub repository
- Select deployment settings
- Deploy!

## Docker Deployment

### 1. Build Docker Image
```bash
docker build -t upsct:latest .
```

### 2. Push to Registry
```bash
docker tag upsct:latest your-registry/upsct:latest
docker push your-registry/upsct:latest
```

### 3. Deploy Container
```bash
docker run -p 5000:5000 -e FLASK_ENV=production your-registry/upsct:latest
```

## Environment Variables

Always set these in production:
```bash
FLASK_ENV=production
SECRET_KEY=your-strong-secret-key
DATABASE_URL=your-database-url
```

## Health Checks

After deployment, verify with:
```bash
curl https://your-app-url/health
```

Expected response:
```json
{"status": "healthy", "message": "UPSCT is running"}
```

## Monitoring

- Monitor logs regularly
- Set up alerts for errors
- Track application performance
- Review health metrics
