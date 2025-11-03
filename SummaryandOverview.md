# AquaVaults Swapper Summary and Overview

### There is no guarantee your swaps will count towards participation on Pond0x. While I have used and tested this swapper there is no guarantee it is safe. Please do your due diligence and use a burner wallet before connecting a main wallet. If you are unfamiliar with code, please copy the Swapper-UI.html file and give it to an AI and ask about its functions and risks.

A web-based Solana token swap interface that allows users to swap between various Solana tokens using the Jupiter Aggregator API, with integrated affiliate vault support. Users can select between two affiliates—Pond0x and AquaVaults—each with their own token vaults and rewards. The app supports manual wallet connection, slippage and fee adjustment, automated bulk swapping, and provides real-time balance and estimated output.


---

## Features

### 1. RPC Configuration

Users can configure their Solana RPC endpoint through an intuitive UI panel (no code editing required).

Supports both Default RPC (public Solana endpoint) and Custom RPC options.

Custom RPC endpoints from providers like Helius, QuickNode, or Alchemy can be entered directly.

RPC configuration is saved automatically in browser storage and persists across sessions.

Users can change RPC at any time using the "Change RPC" button.

Main content is disabled until RPC is properly configured.



### 2. Affiliate Selection

Users can toggle between Pond0x and AquaVaults as the affiliate for swaps.

Each affiliate has dedicated token vaults for different supported tokens.

Active affiliate and vault are clearly displayed in the UI.



### 3. Wallet Integration

Supports manual connection via a Solana wallet (e.g., Phantom).

Displays connected wallet public key, or disconnected state.

Updates token balances in real-time for the selected input token.



### 4. Token Swapping

Supports swaps between multiple Solana tokens:
SOL, USDC, USDT, wPOND, hSOL, mSOL, PepeOnSOL.

Uses the Jupiter Aggregator API to fetch swap quotes and perform swaps.

Includes platform fee and slippage control.

Automatically applies the correct affiliate vault for fee collection.

Provides transaction status updates, confirmation animation, and Solscan link after completion.



### 5. Auto Swap Control

Automated bulk swapping with configurable parameters:

**Number of Swaps**: Execute multiple swaps sequentially (1-1000).

**Wait Time**: Configurable delay between swaps (0-300 seconds).

**Random Amount**: Optional randomization of swap amounts per transaction.

**Min/Max Range**: Set minimum and maximum amounts for random generation.

**Progress Tracking**: Real-time progress display showing current swap number and countdown timer.

**Stop Control**: Ability to cancel auto swap sequence at any time.

Auto swap panel visually indicates when active with color-coded borders.

All controls disabled during auto swap execution to prevent conflicts.



### 6. Fee and Slippage Controls

Adjustable platform fee (in basis points, displayed as %).

Adjustable slippage tolerance (in basis points, displayed as %).

Dynamic estimated output based on current fee/slippage settings.



### 7. Debugging and Logging

Optional debug panel for viewing detailed logs of swap preparation, vault selection, and API responses.

Logs all key events and errors with timestamps.



### 8. Responsive and Accessible UI

Minimal, clean interface with modern design using CSS grid and flexbox.

Highlighted affiliate badges and animated transaction status.

Input fields and buttons styled for clarity and usability.

Visual feedback for RPC configuration status and auto swap activity.



### 9. Wallet data / private keys

window.solana.connect() — relies on the browser wallet (e.g., Phantom).

There is no need for private keys in the file.



### 10. Referral program ID

const REFERRAL_PROGRAM_ID = "JUP6LkbZbjS1jKKwapdHNy74zcZ3tLUZoi5QNyVTaV4";

This is a public Jupiter program ID.



### 11. Local storage / persistent settings

localStorage.setItem; — stores RPC configuration and affiliate preference (UI settings only, not sensitive info).






---

## How It Works

### 1. RPC Configuration Flow

1. User opens the application and sees RPC Configuration panel.


2. User selects either Default RPC or Custom RPC option.


3. If Custom RPC selected, user enters their RPC endpoint URL.


4. User clicks "Confirm RPC" to initialize connection.


5. Configuration is saved automatically to browser storage.


6. Main application content becomes enabled after successful configuration.




### 2. Affiliate Vaults

Each affiliate has a set of pre-configured vault addresses for supported tokens.

When a user selects a token and affiliate, the app automatically maps to the correct vault.



### 3. Swap Flow

1. User configures RPC endpoint (if not already configured).


2. User selects input token, output token, amount, and affiliate.


3. User connects their Solana wallet manually.


4. App fetches a quote from Jupiter API including fee and slippage adjustments.


5. User clicks Swap: the transaction is signed by the wallet and sent to Solana.


6. Status updates reflect progress: preparing → building → wallet approval → sending → confirming → success.




### 4. Auto Swap Flow

1. User enables Auto Swap Control by checking the toggle.


2. User configures swap count and wait time between swaps.


3. (Optional) User enables random amount generation and sets min/max range.


4. User clicks "Start Auto Swap" to begin automated sequence.


5. App executes swaps sequentially with progress tracking and countdown timer.


6. User can stop the sequence at any time using "Stop Auto Swap" button.


7. Final summary displays completed and failed swap counts.




### 5. Real-time Updates

Input token balance updates automatically after swaps or token selection.

Estimated output updates automatically when the amount, fee, or slippage changes.

Auto swap progress and countdown displayed in real-time during execution.





---


## Supported Tokens & Vaults


| Token        | Pond0x Token Vault                        | AquaVaults Token Vault                       |
|--------------|------------------------------------|----------------------------------------|
| SOL          | 9hCLuXrQrHCU9i7y648Nh7uuWKHUsKDiZ5zyBHdZPWtG | 2qcR7nCVRmpxHCYTdQ6G1DjNcDzgEq9eQ1ZrxcmjeVy9 |
| USDC         | 6NqvoPpSYCPEtLEukQaSNs7mS3yK6k285saH9o3vgC96 | 4en3gmtiPtmiHCi5mwT1TrATj4jNe7woJPZLQaWv6Ezu |
| USDT         | 5LmFGjbae5iWejFVT8UiRLggh1me22nTetmere8SjwKy | 5wV1qSp8n9z5DEGHV6JJoEoxdYeBrnVCtP9LbD4Vwx7D |
| wPOND        | GKHmDYWPE8Bf74xDntnpx4hi4H7pRp3HK5QYvPyXGEiU | E4s4KzRBvYQxpFR1L7z7cLDtT814i7bqWFSGgqCDBCn9 |
| hSOL         | 4jkVjzXtrCuxQus3neMtLfNL4wZhsPmm9fKGXoLMXqsG | 54GcC3SjZzavvVJ5ipFfCvQHNnpPRsJLXUdfxNmeJHHm |
| mSOL         | Not supported                       | 49URcyxPiaKRgoEAWfDtJHGWcZus3SVkF39b9Szf3XqC |
| PepeOnSOL    | 3qGSU2RySrjvQ2iGMts2HZ4ssGVSrBUSGL4jN7LHGhgo | Ff7tzrabm8sxHbL4cTmBDby2EQvvtab6NTh56R69u6KS |



---

## Configuration


1. RPC Endpoint

**No code editing required** - RPC is configured through the UI:

Select "Default RPC" for public Solana endpoint, or "Custom RPC" for your own provider.

Enter custom RPC URL directly in the input field (e.g., from Helius, QuickNode, Alchemy).

Configuration is saved automatically and persists across browser sessions.




2. Platform Fee & Slippage

Controlled via number inputs in the UI.

Displayed dynamically in percentage.



3. Affiliate Vault Toggle

Default affiliate: Pond0x.

Checkbox toggles between Pond0x and AquaVaults.

Automatically updates vault addresses and UI labels.

Selection is saved to browser storage.




4. Auto Swap Settings

Configured entirely through the UI:

Number of swaps (1-1000)

Wait time between swaps (0-300 seconds)

Optional random amount generation with min/max range

All settings adjustable before starting auto swap sequence






---

## How to Use

1. Open the HTML file in a browser with a Solana wallet extension (e.g., Phantom).


2. Configure your RPC endpoint using the RPC Configuration panel (select Default or enter Custom RPC URL).


3. Select the input token, output token, and amount to swap.


4. Choose your affiliate by toggling the checkbox.


5. Click Connect Wallet and approve connection in your wallet.


6. Review estimated output and adjust fee/slippage if needed.


7. Click Swap and confirm the transaction in your wallet.


8. (Optional) Enable Auto Swap Control to execute multiple swaps automatically.


9. Track progress in the status box. View the transaction on Solscan once confirmed.



---

## Core Functions

| Function | Description |
|----------|-------------|
| selectRpcOption(option) | Updates UI to show selected RPC option (default or custom) |
| setRpcEndpoint() | Initializes Solana connection with selected RPC and saves to storage |
| changeRpc() | Resets RPC configuration and disables main content |
| updateAffiliateDisplay() | Updates UI to reflect selected affiliate and active vault |
| getCurrentVaults() | Returns current vaults based on affiliate toggle |
| updateActiveVault() | Displays the vault address for the selected input token |
| connectWallet() | Connects wallet and updates UI |
| disconnectWallet() | Disconnects wallet and resets UI |
| updateBalance() | Fetches and displays user token balance |
| getEstimate() | Fetches swap quote and updates estimated output |
| swap(overrideAmount) | Builds, signs and sends swap transaction; handles UI status updates |
| startAutoSwap() | Initiates automated swap sequence with configured parameters |
| stopAutoSwap() | Cancels auto swap sequence and resets UI |
| countdown(seconds) | Displays countdown timer between auto swaps |
| debugLog(msg) | Logs internal swap events for debugging |



---

## Dependencies

Python or Node.js to run a local server

Solana Web3.js via CDN

Jupiter Aggregator API (https://lite-api.jup.ag)

A browser wallet like Phantom or compatible Solana wallet



---

## Notes

All amounts are displayed in UI-friendly units with token-specific decimals.

Only tokens with configured vaults per affiliate can be used for swaps.

Fee and slippage are represented in basis points (bps); 100 bps = 1%.

Error handling is implemented for API errors, wallet connection issues, and missing vaults.

RPC configuration must be completed before wallet connection or swapping.

Auto swap feature requires wallet connection and valid RPC configuration.

Random amount generation uses Math.random() for variation within user-defined min/max range.

Auto swap progress includes real-time countdown and can be cancelled at any time.
