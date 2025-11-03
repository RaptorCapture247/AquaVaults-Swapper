# AquaVaults Swapper Setup Guide
---

🪐 Running the AquaVaults HTML Swapper Locally (Phantom + Custom RPC)

This project is a single HTML file that must be served via a local server to connect to Phantom Wallet and a Solana RPC. Opening it directly in the browser will not work.

This guide walks you through downloading the file, setting up Python, and running it locally.

Please see https://github.com/RaptorCapture247/AquaVaults-Swapper/blob/main/SummaryandOverview.md for technical details.

> You will need an autoclicker of some kind to click the wallet popups while using the Auto Swapper function. You can use a generic clicker such as OPautoclicker or use one of my PyatuoGUI clickers found at: [Windows-Pyatuo-Auto-Clicker](https://github.com/RaptorCapture247/Windows-Pyatuo-Auto-Clicker) / [Mac-PyAuto-Auto-Clicker](https://github.com/RaptorCapture247/Mac-PyAuto-Auto-Clicker)


---

## There is no guarantee your swaps will count towards participation on Pond0x. While I have used and tested this swapper there is no guarantee it is safe. Please do your due diligence and use a burner wallet before connecting a main wallet. If you are unfamiliar with code, please copy the Swapper-UI.html file and give it to an AI and ask about its functions and risks.


---

Step 1 – Download the HTML File from GitHub

1. Go to the GitHub repository where this README is located.


2. Locate the HTML file called Swapper-UI.html.


3. Download it and save it exactly as:

Swapper-UI.html

Windows: Downloads or Desktop

Mac: Downloads or Desktop


> ✅ Using the exact filename ensures all instructions below work without needing to adjust the URL.

> You do not need to download this entire github repository. Go to the repository and either download the file directly or copy the code to a text editor to save as a .html file.



---

Step 2 – Install Python (for local server)

Python allows us to run a local web server so the HTML can connect to Phantom Wallet.


Latest Python release 10/31/2025

https://www.python.org/downloads/release/python-3140/

Windows

1. Go to Python Downloads for Windows.


2. Click Download Python 3.x.x.


3. Run the installer:

✅ Check "Add Python to PATH" before clicking Install.



Mac

1. Open Terminal (Applications → Utilities).


2. Check if Python 3 is installed:



python3 --version

If a version appears, you're ready.

If not, download Python from Python Downloads for Mac and follow the installer.



---

Step 3 – Open Terminal / Command Prompt

Windows: Press Win + R, type cmd, and hit Enter.

Mac: Open Terminal (Applications → Utilities).


Windows Users – How to Find Your Username

1. Open File Explorer and navigate to your Downloads or Desktop folder.


2. Look at the folder path at the top. It should look like:



C:\Users\YourName\Downloads


3. The part after C:\Users\ is your Windows username (replace YourName).



Navigate to the Folder in Terminal

Windows Example

cd C:\Users\YourName\Downloads

Mac Example

cd ~/Downloads

> Tip: You can drag the folder into the terminal after typing cd  to automatically fill the path.




---

Step 4 – Start the Local Server

Run:

python3 -m http.server

or

python -m http.server

You should see:

Serving HTTP on :: port 8000 ...

> Keep this terminal open while using the project.




---

Step 5 – Open the File in Your Browser

1. Open your browser.


2. Go to:



http://localhost:8000/Swapper-UI.html



> Phantom Wallet must be installed and unlocked. Opening directly (double-clicking) will not work.




---

Step 6 – Configure RPC Endpoint

When you first open the swapper, you'll see the RPC Configuration panel at the top:

1. Choose your RPC option:

**Default RPC**: Uses the public Solana RPC (free, may be slower)

**Custom RPC**: Use your own RPC provider (recommended for better performance)


2. If using Custom RPC:

Enter your RPC endpoint URL (e.g., from Helius, QuickNode, Alchemy)

Click "Confirm RPC"


3. Your RPC choice is saved automatically and remembered for future sessions.


4. To change RPC later, click "Change RPC" button.



> ⚡ **Recommended**: Use a custom RPC from providers like Helius (https://helius.dev) or QuickNode for faster, more reliable performance.




---

Step 7 – (Mac Only) Permissions

If macOS asks: "Python wants to accept incoming network connections" → click Allow

If asked for folder access → click OK

If Python is blocked → System Settings → Privacy & Security → Allow Anyway



---

Step 8 – Stop the Server

Press:

Ctrl + C

in the terminal when finished.


---

✅ You're Done!

The AquaVaults Swapper (Swapper-UI.html) is running locally.

Phantom Wallet can be connected.

RPC endpoint is configured through the UI (no code editing needed).


Troubleshooting Tips:

Make sure you've configured an RPC endpoint in the UI before trying to connect your wallet.

Ensure Phantom Wallet is installed, unlocked, and the page is served via localhost.

Check the terminal is still running the local server.

If using a custom RPC, verify your endpoint URL is correct and has sufficient credits/quota.
