# Aqua-Vaults-Swapper
---

🪐 Running the HTML Project Locally (Phantom + Helius RPC)

This project is a single HTML file that must be served via a local server to connect to Phantom Wallet and a Solana RPC via Helius. Opening it directly in the browser will not work.

This guide walks you through downloading the file, setting up Python, adding your Helius RPC, and running it locally.


---

Step 1 — Download the HTML File from GitHub

1. Go to the GitHub repository where this README is located.


2. Locate the HTML file called Swapper UI.html.


3. Download it and save it exactly as:



Swapper UI.html

Windows: Downloads or Desktop

Mac: Downloads or Desktop


> ✅ Using the exact filename ensures all instructions below work without needing to adjust the URL.




---

Step 2 — Install Python (for local server)

Python allows us to run a local web server so the HTML can connect to Phantom Wallet.

Windows

1. Go to Python Downloads for Windows.


2. Click Download Python 3.x.x.


3. Run the installer:

✅ Check “Add Python to PATH” before clicking Install.




Mac

1. Open Terminal (Applications → Utilities).


2. Check if Python 3 is installed:



python3 --version

If a version appears, you’re ready.

If not, download Python from Python Downloads for Mac and follow the installer.



---

Step 3 — Get a Helius RPC Endpoint

1. Go to Helius API portal and sign up.


2. Create a Solana RPC API key.


3. Copy your endpoint URL:


---

Step 4 — Open the HTML File in a Text Editor

You need to edit the file to add your Helius RPC URL.

Windows

1. Right-click Swapper UI.html → Open with → Notepad (or VS Code, Notepad++).


2. Press Ctrl + F and search for:


"Your Personal RPC"


3. Replace it with your Helius RPC URL:


4. Save the file (Ctrl + S).



Mac

1. Right-click Swapper UI.html → Open With → TextEdit (or VS Code).


2. Press Command + F and search for:


"Your Personal RPC"


3. Replace it with your Helius RPC URL and save (Command + S).



> ✅ This ensures users know exactly where to place their RPC without touching other code.




---

Step 5 — Open Terminal / Command Prompt

Windows: Press Win + R, type cmd, and hit Enter.

Mac: Open Terminal (Applications → Utilities).


Windows Users — How to Find Your Username

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

Step 6 — Start the Local Server

Run:

python3 -m http.server

or

python -m http.server

You should see:

Serving HTTP on :: port 8000 ...

> Keep this terminal open while using the project.




---

Step 7 — Open the File in Your Browser

1. Open your browser.


2. Go to:



http://localhost:8000/Swapper UI.html

> Phantom Wallet must be installed and unlocked. Opening directly (double-clicking) will not work.




---

Step 8 — (Mac Only) Permissions

If macOS asks: “Python wants to accept incoming network connections” → click Allow

If asked for folder access → click OK

If Python is blocked → System Settings → Privacy & Security → Allow Anyway



---

Step 9 — Stop the Server

Press:

Ctrl + C

in the terminal when finished.


---

✅ You’re Done!

Your HTML project (Swapper UI.html) is running locally.

Phantom Wallet is connected.

Helius RPC endpoint is active.


Troubleshooting Tips:

Make sure the RPC URL replaced Your Personal RPC in the HTML file.

Ensure Phantom Wallet is installed, unlocked, and the page is served via localhost.

Check the terminal is still running the local server.