# Aqua Vaults Swapper

## There is no guarantee your swaps will count towards participation on Pond0x. While I have used and tested this swapper extensively there is no guarantee it is safe. Please do your due diligence and use a burner wallet before connecting a main wallet.

A web-based Solana token swap interface that allows users to swap between various Solana tokens using the Jupiter Aggregator API, with integrated affiliate vault support. Users can select between two affiliates—Pond0x and Aqua Vaults—each with their own token vaults and rewards. The app supports manual wallet connection, slippage and fee adjustment, and provides real-time balance and estimated output.


---

## Features

### 1. Affiliate Selection

Users can toggle between Pond0x and Aqua Vaults as the affiliate for swaps.

Each affiliate has dedicated token vaults for different supported tokens.

Active affiliate and vault are clearly displayed in the UI.



### 2. Wallet Integration

Supports manual connection via a Solana wallet (e.g., Phantom).

Displays connected wallet public key, or disconnected state.

Updates token balances in real-time for the selected input token.



### 3. Token Swapping

Supports swaps between multiple Solana tokens:
SOL, USDC, USDT, wPOND, hSOL, mSOL, PepeOnSOL.

Uses the Jupiter Aggregator API to fetch swap quotes and perform swaps.

Includes platform fee and slippage control.

Automatically applies the correct affiliate vault for fee collection.

Provides transaction status updates, confirmation animation, and Solscan link after completion.



### 4. Fee and Slippage Controls

Adjustable platform fee (in basis points, displayed as %).

Adjustable slippage tolerance (in basis points, displayed as %).

Dynamic estimated output based on current fee/slippage settings.



### 5. Debugging and Logging

Optional debug panel for viewing detailed logs of swap preparation, vault selection, and API responses.

Logs all key events and errors with timestamps.



### 6. Responsive and Accessible UI

Minimal, clean interface with modern design using CSS grid and flexbox.

Highlighted affiliate badges and animated transaction status.

Input fields and buttons styled for clarity and usability.

### 7. Wallet data / private keys

window.solana.connect() — relies on the browser wallet (e.g., Phantom).

There is no need for private keys in the file.


### 8. Referral program ID

const REFERRAL_PROGRAM_ID = "JUP6LkbZbjS1jKKwapdHNy74zcZ3tLUZoi5QNyVTaV4";

This is a public Jupiter program ID.


### 9. Local storage / persistent settings

localStorage.setItem; — stores only UI preference, not sensitive info.






---

## How It Works

### 1. Affiliate Vaults

Each affiliate has a set of pre-configured vault addresses for supported tokens.

When a user selects a token and affiliate, the app automatically maps to the correct vault.



### 2. Swap Flow

1. User selects input token, output token, amount, and affiliate.


2. User connects their Solana wallet manually.


3. App fetches a quote from Jupiter API including fee and slippage adjustments.


4. User clicks Swap: the transaction is signed by the wallet and sent to Solana.


5. Status updates reflect progress: preparing → building → wallet approval → sending → confirming → success.


### 3. Real-time Updates

Input token balance updates automatically after swaps or token selection.

Estimated output updates automatically when the amount, fee, or slippage changes.





---


## Supported Tokens & Vaults


| Token        | Pond0x Vault                        | Aqua Vaults Vault                       |
|--------------|------------------------------------|----------------------------------------|
| SOL          | 9hCLuXrQrHCU9i7y648Nh7uuWKHUsKDiZ5zyBHdZPWtG | 2qcR7nCVRmpxHCYTdQ6G1DjNcDzgEq9eQ1ZrxcmjeVy9 |
| USDC         | 6NqvoPpSYCPEtLEukQaSNs7mS3yK6k285saH9o3vgC96 | 4en3gmtiPtmiHCi5mwT1TrATj4jNe7woJPZLQaWv6Ezu |
| USDT         | 5LmFGjbae5iWejFVT8UiRLggh1me22nTetmere8SjwKy | 5wV1qSp8n9z5DEGHV6JJoEoxdYeBrnVCtP9LbD4Vwx7D |
| wPOND        | 6NqvoPpSYCPEtLEukQaSNs3yK6k285saH9o3vgC96 | E4s4KzRBvYQxpFR1L7z7cLDtT814i7bqWFSGgqCDBCn9 |
| hSOL         | 9hCLuXrQrHCU9i7y648Nh7uuWKHUsKDiZ5zyBHdZPWtG | 54GcC3SjZzavvVJ5ipFfCvQHNnpPRsJLXUdfxNmeJHHm |
| mSOL         | Not supported                       | 49URcyxPiaKRgoEAWfDtJHGWcZus3SVkF39b9Szf3XqC |
| PepeOnSOL    | 3qGSU2RySrjvQ2iGMts2HZ4ssGVSrBUSGL4jN7LHGhgo | Ff7tzrabm8sxHbL4cTmBDby2EQvvtab6NTh56R69u6KS |



---

## Configuration


1. RPC Endpoint

const RPC_ENDPOINTS = ["Your personal RPC"];

Replace "Your personal RPC" with your Solana RPC URL for network connectivity.


2. Platform Fee & Slippage

Controlled via number inputs in the UI.

Displayed dynamically in percentage.



3. Affiliate Vault Toggle

Default affiliate: Pond0x.

Checkbox toggles between Pond0x and Aqua Vaults.

Automatically updates vault addresses and UI labels.





---

## How to Use

1. Open the HTML file in a browser with a Solana wallet extension (e.g., Phantom).


2. Select the input token, output token, and amount to swap.


3. Choose your affiliate by toggling the checkbox.


4. Click Connect Wallet and approve connection in your wallet.


5. Review estimated output and adjust fee/slippage if needed.


6. Click Swap and confirm the transaction in your wallet.


7. Track progress in the status box. View the transaction on Solscan once confirmed.



---

## Core Functions

Function	Description

(updateAffiliateDisplay)- 	Updates UI to reflect selected affiliate and active vault.

(getCurrentVaults)- Returns current vaults based on affiliate toggle.

(updateActiveVault)-	Displays the vault address for the selected input token.

(connectWallet)- Connects wallet and updates UI.

(disconnectWallet)- Disconnects wallet and resets UI.

(updateBalance)- Fetches and displays user token balance.

(getEstimate)	- Fetches swap quote and updates estimated output.

(swap)- Builds,signs and sends swap transaction; handles UI status updates.

debugLog(msg)	- Logs internal swap events for debugging.



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