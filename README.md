# AquaVaults Swapper Setup Guide
---

🪐 Running the AquaVaults HTML Swapper Locally (Phantom + Custom RPC + Jupiter API)

This project is a single HTML file that must be served via a local server to connect to Phantom Wallet and a Solana RPC. Opening it directly in the browser will not work.

This guide walks you through downloading the file, setting up Python, and running it locally.

Please see https://github.com/RaptorCapture247/AquaVaults-Swapper/blob/main/SummaryandOverview.md for technical details.

> You will need an autoclicker of some kind to click the wallet popups while using the Auto Swapper function. You can use a generic clicker such as OPautoclicker or use one of my PyatuoGUI clickers found at: [Windows-Pyatuo-Auto-Clicker](https://github.com/RaptorCapture247/Windows-Pyatuo-Auto-Clicker) / [Mac-PyAuto-Auto-Clicker](https://github.com/RaptorCapture247/Mac-PyAuto-Auto-Clicker)


---

## ⚠️ IMPORTANT: Jupiter API Migration (December 2024)

**Jupiter has migrated to an authenticated API system. You MUST obtain a FREE API key to use this swapper.**

### What Changed?
- ✅ **NEW REQUIREMENT**: Jupiter API key (free, takes 2 minutes to get)
- ✅ **Migration Deadline**: December 31, 2025
- ✅ **Free Tier**: 60 requests per minute (plenty for normal use)
- ✅ **One-Time Setup**: Configure once, works forever

### Get Your FREE Jupiter API Key (Required)

**Before you can use the swapper, you need an API key:**

1. Visit **https://portal.jup.ag**
2. Click "Connect via Email"
3. Enter your email and verify
4. Click "Generate API Key"
5. **Copy and save your API key** (you'll need it in Step 7)

> 🔑 **This is required** - The swapper will not work without an API key after December 31, 2025.


---

## There is no guarantee your swaps will count towards participation on Pond0x. While I have used and tested this swapper there is no guarantee it is safe. Please do your due diligence and use a burner wallet before connecting a main wallet. If you are unfamiliar with code, please copy the Swapper-UI.html file and give it to an AI and ask about its functions and risks.


---

## Step 1 – Download the HTML File from GitHub

1. Go to the GitHub repository where this README is located.

2. Locate the HTML file called **Swapper-UI.html** (or **AVS-ezRPC2-migrated.html** for the API-enabled version).

3. Download it and save it exactly as:

   **Swapper-UI.html**

   - Windows: Downloads or Desktop
   - Mac: Downloads or Desktop

> ✅ Using the exact filename ensures all instructions below work without needing to adjust the URL.

> You do not need to download this entire github repository. Go to the repository and either download the file directly or copy the code to a text editor to save as a .html file.


---

## Step 2 – Install Python (for local server)

Python allows us to run a local web server so the HTML can connect to Phantom Wallet.

**Latest Python release 10/31/2025**

https://www.python.org/downloads/release/python-3140/

### Windows

1. Go to Python Downloads for Windows.

2. Click Download Python 3.x.x.

3. Run the installer:

   ✅ Check "Add Python to PATH" before clicking Install.

### Mac

1. Open Terminal (Applications → Utilities).

2. Check if Python 3 is installed:

   ```bash
   python3 --version
   ```

   If a version appears, you're ready.

   If not, download Python from Python Downloads for Mac and follow the installer.


---

## Step 3 – Open Terminal / Command Prompt

- **Windows**: Press Win + R, type `cmd`, and hit Enter.
- **Mac**: Open Terminal (Applications → Utilities).

### Windows Users – How to Find Your Username

1. Open File Explorer and navigate to your Downloads or Desktop folder.

2. Look at the folder path at the top. It should look like:

   ```
   C:\Users\YourName\Downloads
   ```

3. The part after `C:\Users\` is your Windows username (replace YourName).

### Navigate to the Folder in Terminal

**Windows Example**
```bash
cd C:\Users\YourName\Downloads
```

**Mac Example**
```bash
cd ~/Downloads
```

> Tip: You can drag the folder into the terminal after typing `cd ` to automatically fill the path.


---

## Step 4 – Start the Local Server

Run:

```bash
python3 -m http.server
```

or

```bash
python -m http.server
```

You should see:

```
Serving HTTP on :: port 8000 ...
```

> Keep this terminal open while using the project.


---

## Step 5 – Open the File in Your Browser

1. Open your browser.

2. Go to:

   ```
   http://localhost:8000/Swapper-UI.html
   ```

> Phantom Wallet must be installed and unlocked. Opening directly (double-clicking) will not work.


---

## Step 6 – Configure Jupiter API Key (NEW - REQUIRED)

When you first open the swapper, you'll see the **Jupiter API Key Configuration** panel at the top:

### Configure Your API Key

1. **Enter Your API Key**
   - Paste the API key you got from https://portal.jup.ag
   - Click "Confirm API Key"

2. **Verify Configuration**
   - Status should change to "✅ Configured"
   - You'll see a masked version of your key (e.g., `abcd1234...xyz9`)

3. **Your API Key is Saved**
   - Stored locally in your browser
   - Automatically loaded on future visits
   - Can be changed anytime by clicking "Change API Key"

> 🔑 **Security Note**: Your API key is stored locally in your browser and only sent to Jupiter's API for authentication. It is never shared with anyone else.

> ⚠️ **Important**: You MUST configure the API key before you can configure RPC or connect your wallet.


---

## Step 7 – Configure RPC Endpoint

After configuring your API key, you'll see the **RPC Configuration** panel:

### Choose Your RPC

1. **Select RPC Option:**

   - **Default RPC**: Uses the public Solana RPC (free, may be slower)
   - **Custom RPC**: Use your own RPC provider (recommended for better performance)

2. **If Using Custom RPC:**
   - Enter your RPC endpoint URL (e.g., from Helius, QuickNode, Alchemy)
   - Click "Confirm RPC"

3. **Your RPC choice is saved automatically** and remembered for future sessions.

4. To change RPC later, click "Change RPC" button.

> ⚡ **Recommended**: Use a custom RPC from providers like Helius (https://helius.dev) or QuickNode for faster, more reliable performance.


---

## Step 8 – Connect Wallet and Start Swapping

1. **Connect Phantom Wallet**
   - Click "Connect Wallet"
   - Approve the connection in Phantom

2. **Choose Your Affiliate**
   - Toggle between Pond0x (swap rewards & mining boost) or AquaVaults (support development)

3. **Configure Your Swap**
   - Select tokens (From/To)
   - Enter amount
   - Adjust slippage and fees if needed

4. **Execute Swap**
   - Click "Swap"
   - Approve transaction in Phantom
   - Wait for confirmation

### Optional: Auto Swap Features

- Check "🤖 Enable Auto Swap Control" to access automated swapping
- Configure number of swaps, wait time, and optional random amounts
- Use with an auto-clicker for fully automated operation


---

## Step 9 – (Mac Only) Permissions

If macOS asks:
- "Python wants to accept incoming network connections" → click **Allow**
- If asked for folder access → click **OK**
- If Python is blocked → System Settings → Privacy & Security → **Allow Anyway**


---

## Step 10 – Stop the Server

When finished, press:

```
Ctrl + C
```

in the terminal to stop the server.


---

## ✅ You're Done!

The AquaVaults Swapper is running locally with:
- ✅ Jupiter API authentication configured
- ✅ RPC endpoint configured through the UI
- ✅ Phantom Wallet connection ready
- ✅ Full swapping functionality available


---

## Troubleshooting Tips

### "Please configure Jupiter API key first"
**Solution**: You need to enter your API key from portal.jup.ag in the Jupiter API Key panel before you can proceed.

### "401 Unauthorized" errors
**Solution**: Your API key may be incorrect. Click "Change API Key" and re-enter it.

### Cannot configure RPC
**Solution**: Make sure you've configured your Jupiter API key first. The API key is required before RPC setup.

### Rate limit errors
**Problem**: Hitting the 60 requests/minute limit  
**Solution**: Use longer wait times in auto swap, or consider upgrading at portal.jup.ag

### Wallet won't connect
**Solution**: 
- Make sure you've configured both API key AND RPC endpoint
- Ensure Phantom Wallet is installed and unlocked
- Verify the page is served via `localhost:8000` not `file://`

### RPC configuration not working
**Solution**: 
- Ensure Phantom Wallet is installed, unlocked
- Check the terminal is still running the local server
- If using custom RPC, verify your endpoint URL is correct and has sufficient credits/quota

### API key not saving
**Problem**: localStorage may be disabled  
**Solution**: 
- Check browser settings allow localStorage
- Try a different browser
- Make sure you're on `localhost:8000` not `file://`


---

## Configuration Summary

### Required Steps (In Order)
1. ✅ Get Jupiter API key from portal.jup.ag
2. ✅ Configure API key in swapper
3. ✅ Configure RPC endpoint
4. ✅ Connect Phantom wallet
5. ✅ Start swapping!

### What Gets Saved
Your configuration is automatically saved in your browser:
- Jupiter API key (masked in UI for security)
- RPC endpoint preference (Default or Custom)
- Custom RPC URL (if using custom)
- Affiliate selection (Pond0x or AquaVaults)

### Subsequent Sessions
On your next visit:
- API key automatically loaded ✅
- RPC settings automatically loaded ✅
- Just connect wallet and swap! ✅


---

## Additional Resources

### Jupiter API
- **Get API Key**: https://portal.jup.ag
- **API Documentation**: https://dev.jup.ag
- **Migration Guide**: https://dev.jup.ag/portal/migrate-from-lite-api
- **Rate Limits**: https://dev.jup.ag/portal/rate-limit

### RPC Providers
- **Helius**: https://helius.dev (recommended)
- **QuickNode**: https://quicknode.com
- **Alchemy**: https://alchemy.com

### Auto-Clickers (for Auto Swap)
- **Windows**: [Windows-Pyatuo-Auto-Clicker](https://github.com/RaptorCapture247/Windows-Pyatuo-Auto-Clicker)
- **Mac**: [Mac-PyAuto-Auto-Clicker](https://github.com/RaptorCapture247/Mac-PyAuto-Auto-Clicker)
- **Generic**: OPautoclicker or similar


---

## FAQ

### Do I need to pay for the Jupiter API key?
**No!** The free tier provides 60 requests per minute, which is plenty for normal use.

### What happens if I don't migrate?
After December 31, 2025, the old API endpoints will stop working and swaps will fail.

### Can I use the same API key on multiple computers?
**Yes!** You can use the same API key across different browsers and computers.

### Is my API key safe?
**Yes** - it's stored locally in your browser and only sent to Jupiter's API for authentication.

### Do I need a custom RPC?
**No, but recommended.** The default RPC works but custom RPCs (Helius, QuickNode) provide better performance.

### How many swaps can I do with the free API tier?
60 requests per minute = approximately 30 swaps per minute (each swap uses 2 requests).


---

## Version Notes

### Current Version Features
- ✅ Jupiter authenticated API (api.jup.ag)
- ✅ API key configuration UI
- ✅ Custom RPC support
- ✅ Dual affiliate system (Pond0x/AquaVaults)
- ✅ Auto swap with random amounts
- ✅ Token vault fee collection
- ✅ Comprehensive error handling

### Migration from Old Version
If you're upgrading from the old swapper:
1. Get your Jupiter API key
2. Download the new version
3. Configure API key (one-time setup)
4. Everything else works the same!


---

**Need Help?** Check the troubleshooting section above or review the detailed migration guide in the repository.

**Ready to Swap?** Follow the steps above and you'll be up and running in 5 minutes! 🚀
