# How to Deploy Your Discord Bot to Railway

Your code is now ready for Railway deployment! Follow these steps:

## Step 1: Enable Message Content Intent in Discord
**IMPORTANT:** This is why your bot wasn't responding to commands before!

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Select your bot application
3. Go to the **Bot** section
4. Scroll down to **Privileged Gateway Intents**
5. **Enable "MESSAGE CONTENT INTENT"** (this is crucial!)
6. Click **Save Changes**

## Step 2: Deploy to Railway

1. Go to [Railway.app](https://railway.app/) and sign in
2. Click **New Project** → **Deploy from GitHub repo**
3. Connect your GitHub account and select this repository
   - If you haven't pushed to GitHub yet, create a new repo and push your code
4. Railway will automatically detect your Procfile and deploy

## Step 3: Add Your Bot Token

1. In Railway, go to your project
2. Click on **Variables**
3. Add a new variable:
   - **Name:** `TOKEN`
   - **Value:** Your Discord bot token (same one you used in Replit)
4. Save the variable

## Step 4: Deploy

1. Railway will automatically redeploy with the new environment variable
2. Check the **Deployments** tab to see if it's running
3. Check the **Logs** to confirm the bot connected successfully
4. Test a command in Discord (like `!helpme`)

## Troubleshooting

### Bot online but not responding?
→ Make sure MESSAGE CONTENT INTENT is enabled in Discord Developer Portal (Step 1 above)

### "failed mise install python" error during deployment?
This project now includes `nixpacks.toml` which should fix this error. If it still fails:

**Option A:** Add this environment variable in Railway:
- Name: `MISE_PYTHON_VERIFY_SIGNATURES`
- Value: `0`

**Option B:** Try redeploying - Railway has automatic fixes for this issue

### Bot offline after deployment?
→ Check Railway logs for errors, verify TOKEN is set correctly

### Still having issues?
→ Check that your bot is invited to your server with proper permissions (Administrator or Send Messages + Read Messages)

## Files in This Repo

- `main.py` - Your Discord bot code
- `requirements.txt` - Python dependencies
- `Procfile` - Tells Railway how to run your bot (worker process)
- `runtime.txt` - Specifies Python 3.11.9
- `nixpacks.toml` - Railway build configuration (fixes Python installation issues)
