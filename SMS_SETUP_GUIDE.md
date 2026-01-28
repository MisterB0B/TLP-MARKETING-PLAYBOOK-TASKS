# SMS Notification Setup Guide

## 📱 Overview

This guide will help you set up SMS notifications for THE LIGHT PARK Task Management System using Twilio. SMS notifications are sent for:
- Task completions
- Note edits

**Target Phone Number**: 17145958391

## 🎯 Quick Start

### Current Status
- ✅ Frontend code is ready and configured
- ✅ SMS logging is active in browser console (development mode)
- 📋 Backend API needs to be deployed for production SMS delivery

### What You Need
1. Twilio account (free trial available)
2. Backend server (Node.js, Python, PHP, etc.)
3. 10-15 minutes for setup

## 🔧 Step-by-Step Setup

### Step 1: Create Twilio Account

1. **Sign Up**
   - Visit: https://www.twilio.com/try-twilio
   - Create a free account
   - Verify your email and phone number

2. **Get Trial Credits**
   - New accounts receive $15 in trial credits
   - Sufficient for testing and initial deployment

3. **Collect Credentials**
   - Go to Twilio Console: https://console.twilio.com/
   - Find your **Account SID** (starts with "AC...")
   - Find your **Auth Token** (click to reveal)
   - Save these securely - you'll need them for the backend

### Step 2: Get a Twilio Phone Number

1. **Purchase Number**
   - In Twilio Console, go to Phone Numbers → Buy a Number
   - Select your country (United States)
   - Choose a number with SMS capabilities
   - Click "Buy" (uses trial credits or paid balance)

2. **Save Your Number**
   - Format: +1XXXXXXXXXX
   - This will be your "from" number for SMS

### Step 3: Verify Target Phone Number (Trial Accounts Only)

If using a trial account, you must verify the recipient number:

1. Go to Phone Numbers → Verified Caller IDs
2. Click "Add a new number"
3. Enter: +17145958391
4. Twilio will send a verification code
5. Enter the code to verify

**Note**: Paid accounts can send to any number without verification.

### Step 4: Set Up Backend API

Choose your preferred backend technology:

#### Option A: Node.js + Express (Recommended)

**1. Install Dependencies**
```bash
npm init -y
npm install express twilio cors dotenv
```

**2. Create `.env` File**
```env
TWILIO_ACCOUNT_SID=your_account_sid_here
TWILIO_AUTH_TOKEN=your_auth_token_here
TWILIO_PHONE_NUMBER=+1234567890
PORT=3000
```

**3. Create `server.js`**
```javascript
require('dotenv').config();
const express = require('express');
const cors = require('cors');
const twilio = require('twilio');

const app = express();
app.use(cors());
app.use(express.json());

// Initialize Twilio client
const client = twilio(
    process.env.TWILIO_ACCOUNT_SID,
    process.env.TWILIO_AUTH_TOKEN
);

// SMS endpoint
app.post('/api/send-sms', async (req, res) => {
    try {
        const { to, message, eventType, task } = req.body;

        // Validate input
        if (!to || !message) {
            return res.status(400).json({
                success: false,
                error: 'Missing required fields: to, message'
            });
        }

        // Send SMS via Twilio
        const result = await client.messages.create({
            body: message,
            from: process.env.TWILIO_PHONE_NUMBER,
            to: to
        });

        console.log(`SMS sent successfully: ${result.sid}`);
        console.log(`Event: ${eventType}, Task: ${task?.title || 'Unknown'}`);

        res.json({
            success: true,
            messageSid: result.sid,
            status: result.status
        });

    } catch (error) {
        console.error('SMS Error:', error);
        res.status(500).json({
            success: false,
            error: error.message
        });
    }
});

// Health check endpoint
app.get('/api/health', (req, res) => {
    res.json({ status: 'OK', service: 'SMS API' });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`SMS API server running on port ${PORT}`);
});
```

**4. Run the Server**
```bash
node server.js
```

**5. Test the API**
```bash
curl -X POST http://localhost:3000/api/send-sms \
  -H "Content-Type: application/json" \
  -d '{
    "to": "+17145958391",
    "message": "Test message from THE LIGHT PARK",
    "eventType": "test",
    "task": {"title": "Test Task"}
  }'
```

#### Option B: Python + Flask

**1. Install Dependencies**
```bash
pip install flask twilio flask-cors python-dotenv
```

**2. Create `.env` File**
```env
TWILIO_ACCOUNT_SID=your_account_sid_here
TWILIO_AUTH_TOKEN=your_auth_token_here
TWILIO_PHONE_NUMBER=+1234567890
```

**3. Create `app.py`**
```python
import os
from flask import Flask, request, jsonify
from flask_cors import CORS
from twilio.rest import Client
from dotenv import load_dotenv

load_dotenv()

app = Flask(__name__)
CORS(app)

# Initialize Twilio client
client = Client(
    os.getenv('TWILIO_ACCOUNT_SID'),
    os.getenv('TWILIO_AUTH_TOKEN')
)

@app.route('/api/send-sms', methods=['POST'])
def send_sms():
    try:
        data = request.json
        to = data.get('to')
        message = data.get('message')
        event_type = data.get('eventType')
        task = data.get('task', {})

        if not to or not message:
            return jsonify({
                'success': False,
                'error': 'Missing required fields'
            }), 400

        # Send SMS
        result = client.messages.create(
            body=message,
            from_=os.getenv('TWILIO_PHONE_NUMBER'),
            to=to
        )

        print(f"SMS sent: {result.sid}")
        print(f"Event: {event_type}, Task: {task.get('title', 'Unknown')}")

        return jsonify({
            'success': True,
            'messageSid': result.sid,
            'status': result.status
        })

    except Exception as e:
        print(f"Error: {str(e)}")
        return jsonify({
            'success': False,
            'error': str(e)
        }), 500

@app.route('/api/health', methods=['GET'])
def health():
    return jsonify({'status': 'OK', 'service': 'SMS API'})

if __name__ == '__main__':
    app.run(port=3000, debug=True)
```

**4. Run the Server**
```bash
python app.py
```

#### Option C: PHP

**1. Install Twilio SDK**
```bash
composer require twilio/sdk
```

**2. Create `sms-api.php`**
```php
<?php
require_once 'vendor/autoload.php';
use Twilio\Rest\Client;

header('Content-Type: application/json');
header('Access-Control-Allow-Origin: *');
header('Access-Control-Allow-Methods: POST');
header('Access-Control-Allow-Headers: Content-Type');

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $data = json_decode(file_get_contents('php://input'), true);
    
    $to = $data['to'] ?? null;
    $message = $data['message'] ?? null;
    
    if (!$to || !$message) {
        http_response_code(400);
        echo json_encode(['success' => false, 'error' => 'Missing fields']);
        exit;
    }
    
    try {
        $sid = getenv('TWILIO_ACCOUNT_SID');
        $token = getenv('TWILIO_AUTH_TOKEN');
        $from = getenv('TWILIO_PHONE_NUMBER');
        
        $client = new Client($sid, $token);
        
        $result = $client->messages->create($to, [
            'from' => $from,
            'body' => $message
        ]);
        
        echo json_encode([
            'success' => true,
            'messageSid' => $result->sid
        ]);
        
    } catch (Exception $e) {
        http_response_code(500);
        echo json_encode([
            'success' => false,
            'error' => $e->getMessage()
        ]);
    }
}
?>
```

### Step 5: Update Frontend Code

1. **Open `index.html`**
2. **Find the `sendSMSNotification` function** (around line 1350)
3. **Uncomment the fetch() call**:

```javascript
function sendSMSNotification(eventType, taskData) {
    const smsData = {
        to: CONFIG.NOTIFICATION_PHONE,
        eventType: eventType,
        task: taskData,
        timestamp: new Date().toISOString(),
        message: formatSMSMessage(eventType, taskData)
    };

    // UNCOMMENT THIS SECTION:
    fetch('http://your-server.com:3000/api/send-sms', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(smsData)
    })
    .then(response => response.json())
    .then(data => {
        console.log('SMS sent successfully:', data);
        showSMSFeedback(eventType);
    })
    .catch(error => {
        console.error('SMS sending failed:', error);
    });
}
```

4. **Replace `http://your-server.com:3000` with your actual backend URL**

### Step 6: Deploy Backend

Choose a hosting platform:

#### Option A: Heroku (Easy, Free Tier Available)
```bash
heroku create your-app-name
heroku config:set TWILIO_ACCOUNT_SID=your_sid
heroku config:set TWILIO_AUTH_TOKEN=your_token
heroku config:set TWILIO_PHONE_NUMBER=your_number
git push heroku main
```

#### Option B: AWS Lambda (Serverless)
- Use AWS Lambda + API Gateway
- Deploy Node.js function
- Configure environment variables

#### Option C: DigitalOcean App Platform
- Connect GitHub repository
- Set environment variables
- Deploy with one click

#### Option D: Your Own Server
- Deploy to VPS (DigitalOcean, Linode, etc.)
- Use PM2 for process management
- Set up Nginx reverse proxy
- Enable HTTPS with Let's Encrypt

### Step 7: Test End-to-End

1. **Complete a task** in the application
2. **Check your phone** for SMS at 17145958391
3. **Edit a note** on a task
4. **Check your phone** again for SMS
5. **Verify console logs** show successful API calls

## 🔍 Troubleshooting

### Issue: SMS Not Received

**Check:**
- [ ] Twilio account has credits
- [ ] Phone number is verified (trial accounts)
- [ ] Backend server is running
- [ ] API endpoint URL is correct in frontend
- [ ] CORS is enabled on backend
- [ ] Check Twilio console logs for errors

### Issue: API Errors

**Check:**
- [ ] Environment variables are set correctly
- [ ] Twilio credentials are valid
- [ ] Phone numbers are in E.164 format (+1XXXXXXXXXX)
- [ ] Backend server logs for detailed errors

### Issue: CORS Errors

**Solution:**
```javascript
// Add to your backend
app.use(cors({
    origin: '*', // Or specify your frontend domain
    methods: ['POST', 'GET'],
    allowedHeaders: ['Content-Type']
}));
```

## 💰 Cost Estimation

### Twilio Pricing (US)
- **SMS**: $0.0079 per message
- **Phone Number**: $1.15/month

### Monthly Cost Examples
- **100 SMS/month**: ~$0.79 + $1.15 = $1.94/month
- **500 SMS/month**: ~$3.95 + $1.15 = $5.10/month
- **1000 SMS/month**: ~$7.90 + $1.15 = $9.05/month

### Free Trial
- $15 credit (enough for ~1,900 messages)
- Perfect for testing and initial deployment

## 🔒 Security Best Practices

1. **Never commit credentials to Git**
   - Use `.env` files
   - Add `.env` to `.gitignore`

2. **Use environment variables**
   - Store credentials securely
   - Different credentials for dev/prod

3. **Implement rate limiting**
   ```javascript
   const rateLimit = require('express-rate-limit');
   
   const limiter = rateLimit({
       windowMs: 15 * 60 * 1000, // 15 minutes
       max: 100 // limit each IP to 100 requests per windowMs
   });
   
   app.use('/api/', limiter);
   ```

4. **Add authentication**
   - API keys for frontend
   - JWT tokens
   - IP whitelisting

5. **Enable HTTPS**
   - Use Let's Encrypt for free SSL
   - Enforce HTTPS in production

## 📊 Monitoring & Logging

### Twilio Console
- View all sent messages
- Check delivery status
- Monitor costs
- Set up alerts

### Backend Logging
```javascript
// Add detailed logging
console.log(`[${new Date().toISOString()}] SMS Request:`, {
    to: to,
    eventType: eventType,
    taskTitle: task?.title
});
```

### Error Tracking
- Use Sentry or similar service
- Track failed SMS attempts
- Monitor API errors

## 🚀 Production Checklist

Before going live:

- [ ] Twilio account upgraded from trial (if needed)
- [ ] Backend deployed to production server
- [ ] Environment variables configured
- [ ] HTTPS enabled
- [ ] CORS properly configured
- [ ] Rate limiting implemented
- [ ] Error monitoring set up
- [ ] Test SMS delivery to 17145958391
- [ ] Frontend updated with production API URL
- [ ] Backup phone number configured (optional)
- [ ] Cost alerts set up in Twilio
- [ ] Documentation updated with production details

## 📞 Support Resources

- **Twilio Documentation**: https://www.twilio.com/docs/sms
- **Twilio Support**: https://support.twilio.com/
- **Twilio Console**: https://console.twilio.com/
- **Status Page**: https://status.twilio.com/

## 🎉 Success!

Once setup is complete, you'll receive SMS notifications at **17145958391** for:
- ✅ Task completions
- ✏️ Note edits

The system will automatically send formatted messages like:
- "THE LIGHT PARK: Task completed - [Task Title]"
- "THE LIGHT PARK: Note edited on task - [Task Title]"