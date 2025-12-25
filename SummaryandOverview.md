# AquaVaults Swapper Summary and Overview

### There is no guarantee your swaps will count towards participation on Pond0x. While I have used and tested this swapper there is no guarantee it is safe. Please do your due diligence and use a burner wallet before connecting a main wallet. If you are unfamiliar with code, please copy the Swapper-UI.html file and give it to an AI and ask about its functions and risks.

A web-based Solana token swap interface that allows users to swap between various Solana tokens using the Jupiter Aggregator API, with integrated affiliate vault support. Users can select between two affiliates—Pond0x and AquaVaults—each with their own token vaults and rewards. The app supports manual wallet connection, slippage and fee adjustment, automated bulk swapping, and provides real-time balance and estimated output.

## ⚠️ Jupiter API Migration Notice

**As of December 2024, Jupiter has migrated to an authenticated API system.**

- **API Endpoint**: Changed from `https://lite-api.jup.ag` to `https://api.jup.ag`
- **Authentication**: API key required (free tier available)
- **Free Tier**: 60 requests per minute
- **Migration Deadline**: December 31, 2025
- **Get API Key**: Visit https://portal.jup.ag

The swapper now requires users to configure a Jupiter API key before use. This is a one-time setup that is saved locally in the browser.

---

## Features

### 1. Jupiter API Key Configuration (NEW)

Users must configure a Jupiter API key before using the swapper.

API key is obtained for free from https://portal.jup.ag (60 requests/min free tier).

Key is entered through an intuitive UI panel with password masking.

API key is stored securely in browser's localStorage and never shared.

Masked display shows only first 8 and last 4 characters for security.

Configuration is validated before allowing RPC or wallet setup.

Users can change API key at any time using the "Change API Key" button.

Main content is disabled until API key is properly configured.


### 2. RPC Configuration

Users can configure their Solana RPC endpoint through an intuitive UI panel (no code editing required).

Supports both Default RPC (public Solana endpoint) and Custom RPC options.

Custom RPC endpoints from providers like Helius, QuickNode, or Alchemy can be entered directly.

RPC configuration is saved automatically in browser storage and persists across sessions.

Users can change RPC at any time using the "Change RPC" button.

**Prerequisite**: Jupiter API key must be configured before RPC setup.

Main content is disabled until both API key and RPC are properly configured.


### 3. Affiliate Selection

Users can toggle between Pond0x and AquaVaults as the affiliate for swaps.

Each affiliate has dedicated token vaults for different supported tokens.

Active affiliate and vault are clearly displayed in the UI.

For swaps to have the potential to count towards participation on Pond0x.com you must use the Pond0x affiliate. Using the AquaVaults affiliate is a good faith option where fees are used towards the development of the AquaVaults token pooling system and have no bearing on Pond0x participation.


### 4. Wallet Integration

Supports manual connection via a Solana wallet (e.g., Phantom).

Displays connected wallet public key, or disconnected state.

Updates token balances in real-time for the selected input token.

**Prerequisite**: Both Jupiter API key and RPC must be configured before wallet connection.


### 5. Token Swapping

Supports swaps between multiple Solana tokens:
SOL, USDC, USDT, wPOND, hSOL, mSOL, PepeOnSOL.

Uses the Jupiter Aggregator API (api.jup.ag) to fetch swap quotes and perform swaps.

All API requests include authentication headers with the user's API key.

Includes platform fee and slippage control.

Automatically applies the correct affiliate vault for fee collection.

Provides transaction status updates, confirmation animation, and Solscan link after completion.


### 6. Auto Swap Control

Automated bulk swapping with configurable parameters:

**Number of Swaps**: Execute multiple swaps sequentially (1-1000).

**Wait Time**: Configurable delay between swaps (0-300 seconds).

**Random Amount**: Optional randomization of swap amounts per transaction.

**Min/Max Range**: Set minimum and maximum amounts for random generation.

**Progress Tracking**: Real-time progress display showing current swap number and countdown timer.

**Stop Control**: Ability to cancel auto swap sequence at any time.

Auto swap panel visually indicates when active with color-coded borders.

All controls disabled during auto swap execution to prevent conflicts.

**Prerequisites**: API key, RPC, and wallet must all be configured before auto swap can start.


### 7. Fee and Slippage Controls

Adjustable platform fee (in basis points, displayed as %).

Adjustable slippage tolerance (in basis points, displayed as %).

Dynamic estimated output based on current fee/slippage settings.


### 8. Debugging and Logging

Optional debug panel for viewing detailed logs of swap preparation, vault selection, and API responses.

Logs all key events and errors with timestamps.

Includes API key configuration events and authentication status.


### 9. Responsive and Accessible UI

Minimal, clean interface with modern design using CSS grid and flexbox.

Highlighted affiliate badges and animated transaction status.

Input fields and buttons styled for clarity and usability.

Visual feedback for API key configuration status, RPC configuration status, and auto swap activity.

Color-coded panels indicate configuration state (inactive: blue border, configured: green border).


### 10. Wallet data / private keys

window.solana.connect() — relies on the browser wallet (e.g., Phantom).

There is no need for private keys in the file.


### 11. Referral program ID

const REFERRAL_PROGRAM_ID = "JUP6LkbZbjS1jKKwapdHNy74zcZ3tLUZoi5QNyVTaV4";

This is a public Jupiter program ID.


### 12. Local storage / persistent settings

localStorage stores:
- Jupiter API key (for authenticated API access)
- RPC configuration (endpoint type and custom URL)
- Affiliate preference (Pond0x or AquaVaults)

All stored data is UI settings and user preferences - no sensitive wallet data is stored.


---

## How It Works

### 1. API Key Configuration Flow (NEW)

1. User opens the application and sees Jupiter API Key Configuration panel at the top.

2. User enters their API key obtained from https://portal.jup.ag.

3. App validates key length (minimum 20 characters).

4. User clicks "Confirm API Key" to save configuration.

5. API key is stored in browser's localStorage with masking in UI.

6. Configuration status updates to "✅ Configured" with green indicator.

7. RPC configuration panel becomes available after API key is configured.


### 2. RPC Configuration Flow

1. User sees RPC Configuration panel (available after API key is configured).

2. User selects either Default RPC or Custom RPC option.

3. If Custom RPC selected, user enters their RPC endpoint URL.

4. User clicks "Confirm RPC" to initialize connection.

5. Configuration is saved automatically to browser storage.

6. Main application content becomes enabled after successful configuration.


### 3. Affiliate Vaults

Each affiliate has a set of pre-configured vault addresses for supported tokens.

When a user selects a token and affiliate, the app automatically maps to the correct vault.


### 4. Swap Flow

1. User configures Jupiter API key (one-time setup, persists across sessions).

2. User configures RPC endpoint (if not already configured).

3. User selects input token, output token, amount, and affiliate.

4. User connects their Solana wallet manually.

5. App fetches a quote from Jupiter API (api.jup.ag) including fee and slippage adjustments.
   - Quote request includes `x-api-key` header for authentication.

6. User clicks Swap: the transaction is built using authenticated API.
   - Swap request includes `x-api-key` header for authentication.

7. Transaction is signed by the wallet and sent to Solana.

8. Status updates reflect progress: preparing → building → wallet approval → sending → confirming → success.


### 5. Auto Swap Flow

1. User enables Auto Swap Control by checking the toggle.

2. User configures swap count and wait time between swaps.

3. (Optional) User enables random amount generation and sets min/max range.

4. User clicks "Start Auto Swap" to begin automated sequence.
   - App validates API key, RPC, and wallet connection before starting.

5. App executes swaps sequentially with progress tracking and countdown timer.
   - Each swap uses authenticated Jupiter API with user's API key.

6. User can stop the sequence at any time using "Stop Auto Swap" button.

7. Final summary displays completed and failed swap counts.


### 6. Real-time Updates

Input token balance updates automatically after swaps or token selection.

Estimated output updates automatically when the amount, fee, or slippage changes.
- Uses authenticated API call with `x-api-key` header.

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

### 1. Jupiter API Key (NEW - REQUIRED)

**No code editing required** - API key is configured through the UI:

Obtain free API key from https://portal.jup.ag (60 requests/minute free tier).

Enter API key in the Jupiter API Key Configuration panel.

Key is validated (minimum 20 characters) and saved to browser localStorage.

Masked display in UI shows format: `abcd1234...xyz9` for security.

Can be changed at any time using "Change API Key" button.

**Must be configured before RPC, wallet connection, or swapping.**


### 2. RPC Endpoint

**No code editing required** - RPC is configured through the UI:

Select "Default RPC" for public Solana endpoint, or "Custom RPC" for your own provider.

Enter custom RPC URL directly in the input field (e.g., from Helius, QuickNode, Alchemy).

Configuration is saved automatically and persists across browser sessions.

**Prerequisite**: Jupiter API key must be configured first.


### 3. Platform Fee & Slippage

Controlled via number inputs in the UI.

Displayed dynamically in percentage.


### 4. Affiliate Vault Toggle

Default affiliate: Pond0x.

Checkbox toggles between Pond0x and AquaVaults.

Automatically updates vault addresses and UI labels.

Selection is saved to browser storage.


### 5. Auto Swap Settings

Configured entirely through the UI:

Number of swaps (1-1000)

Wait time between swaps (0-300 seconds)

Optional random amount generation with min/max range

All settings adjustable before starting auto swap sequence


---

## How to Use

1. Open the HTML file in a browser with a Solana wallet extension (e.g., Phantom).

2. **Configure Jupiter API key** (NEW - REQUIRED):
   - Enter your API key from https://portal.jup.ag
   - Click "Confirm API Key"

3. Configure your RPC endpoint using the RPC Configuration panel (select Default or enter Custom RPC URL).

4. Select the input token, output token, and amount to swap.

5. Choose your affiliate by toggling the checkbox.

6. Click Connect Wallet and approve connection in your wallet.

7. Review estimated output and adjust fee/slippage if needed.

8. Click Swap and confirm the transaction in your wallet.

9. (Optional) Enable Auto Swap Control to execute multiple swaps automatically.

10. Track progress in the status box. View the transaction on Solscan once confirmed.


---

## Core Functions

| Function | Description |
|----------|-------------|
| setApiKey() | Validates and saves Jupiter API key to localStorage |
| updateApiKeyDisplay() | Updates UI to show masked API key and configuration status |
| changeApiKey() | Resets API key configuration and disables dependent features |
| selectRpcOption(option) | Updates UI to show selected RPC option (default or custom) |
| setRpcEndpoint() | Initializes Solana connection with selected RPC and saves to storage (requires API key) |
| changeRpc() | Resets RPC configuration and disables main content |
| updateAffiliateDisplay() | Updates UI to reflect selected affiliate and active vault |
| getCurrentVaults() | Returns current vaults based on affiliate toggle |
| updateActiveVault() | Displays the vault address for the selected input token |
| connectWallet() | Connects wallet and updates UI (requires API key and RPC) |
| disconnectWallet() | Disconnects wallet and resets UI |
| updateBalance() | Fetches and displays user token balance |
| getEstimate() | Fetches swap quote from authenticated API and updates estimated output |
| swap(overrideAmount) | Builds, signs and sends swap transaction using authenticated API; handles UI status updates |
| startAutoSwap() | Initiates automated swap sequence with configured parameters (validates API key) |
| stopAutoSwap() | Cancels auto swap sequence and resets UI |
| countdown(seconds) | Displays countdown timer between auto swaps |
| debugLog(msg) | Logs internal swap events for debugging |


---

## API Integration

### Jupiter Aggregator API

**Base URL**: `https://api.jup.ag` (migrated from lite-api.jup.ag)

**Authentication**: Required via `x-api-key` header

**Endpoints Used**:

1. **Quote Endpoint**: `/swap/v1/quote`
   - Fetches swap quotes with fee and slippage parameters
   - Requires API key authentication
   - Used for: Estimated output display, swap preparation

2. **Swap Endpoint**: `/swap/v1/swap`
   - Builds swap transaction with user parameters
   - Requires API key authentication
   - Used for: Transaction creation and execution

**Request Headers**:
```javascript
{
  "Content-Type": "application/json",
  "x-api-key": "user-api-key-here"
}
```

**Rate Limits**:
- Free tier: 60 requests per minute
- Each swap uses 2 requests (1 quote + 1 swap)
- Approximately 30 swaps per minute maximum on free tier


---

## Dependencies

Python or Node.js to run a local server

Solana Web3.js via CDN

**Jupiter Aggregator API** (https://api.jup.ag) with API key authentication

**Jupiter API Portal** (https://portal.jup.ag) for obtaining API keys

A browser wallet like Phantom or compatible Solana wallet


---

## Security Considerations

### API Key Security

API key is stored in browser's localStorage (client-side only).

Key is never transmitted except to Jupiter's official API endpoints.

UI displays masked version to prevent shoulder-surfing.

Users can change or remove API key at any time.

No backend server involved - all authentication is client-side.


### Wallet Security

No private keys are stored or handled by the application.

All transaction signing is performed by the user's wallet extension.

Users maintain full control over transaction approval.


### Local Storage

Only stores non-sensitive configuration data:
- Jupiter API key (for API authentication)
- RPC endpoint preferences
- Affiliate selection
- UI settings

No wallet addresses, private keys, or transaction data is stored.


---

## Notes

All amounts are displayed in UI-friendly units with token-specific decimals.

Only tokens with configured vaults per affiliate can be used for swaps.

Fee and slippage are represented in basis points (bps); 100 bps = 1%.

Error handling is implemented for API errors, wallet connection issues, missing vaults, and authentication failures.

**API key must be configured before any other setup steps.**

RPC configuration must be completed before wallet connection or swapping.

Auto swap feature requires API key, RPC configuration, and wallet connection.

Random amount generation uses Math.random() for variation within user-defined min/max range.

Auto swap progress includes real-time countdown and can be cancelled at any time.

**Migration Note**: Old swapper using lite-api.jup.ag will stop working December 31, 2025. Users must migrate to api.jup.ag with API key authentication.


---

## Configuration Flow Summary

**Required Setup Order**:
1. ✅ Configure Jupiter API Key (one-time, persists)
2. ✅ Configure RPC Endpoint (one-time, persists)
3. ✅ Connect Phantom Wallet (each session)
4. ✅ Ready to swap!

**Subsequent Sessions**:
- API key auto-loads from localStorage
- RPC settings auto-load from localStorage
- Only wallet connection required
- All other settings persist


---

## Troubleshooting

### Common Issues

**"Please configure Jupiter API key first"**
- Solution: Enter API key from portal.jup.ag in the top panel

**"401 Unauthorized" errors**
- Solution: API key may be invalid - regenerate at portal.jup.ag

**"Cannot configure RPC"**
- Solution: Configure API key first - it's a prerequisite

**Rate limit errors (429)**
- Solution: Wait 1 minute or upgrade API key tier at portal.jup.ag
- Note: Each swap uses 2 API calls (quote + swap)

**Swap fails with no error**
- Check: API key is valid
- Check: RPC is configured and working
- Check: Wallet is connected
- Check: Token has vault for selected affiliate


---

## Version History

### Current Version (December 2024)
- ✅ Migrated to Jupiter authenticated API (api.jup.ag)
- ✅ Added API key configuration UI
- ✅ Updated all API calls to include authentication headers
- ✅ Enhanced security with API key masking
- ✅ Maintained all existing swap and auto-swap features

### Previous Version
- ❌ Used lite-api.jup.ag (deprecated December 31, 2025)
- ❌ No API key required (no longer supported)
