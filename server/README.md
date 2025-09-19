# Nad Racer Backend - Score Submission System

Backend server for Nad Racer that handles secure blockchain score submissions using the Monad testnet.

## Features

- ✅ **Secure Score Submissions** - Server-side validation prevents cheating
- ✅ **Onchain Storage** - All scores stored permanently on Monad blockchain
- ✅ **Rate Limiting** - Prevents abuse and spam
- ✅ **Input Validation** - Comprehensive security checks
- ✅ **Player Data Retrieval** - Fetch individual player statistics

## Setup

### 1. Install Dependencies
```bash
cd backend
npm install
```

### 2. Environment Configuration
```bash
cp .env.example .env
```

Edit `.env` with your configuration:
```env
# Server Configuration
PORT=3001
NODE_ENV=development
FRONTEND_URL=http://localhost:5173

# Game Configuration (set after game registration)
GAME_ADDRESS=0x0000000000000000000000000000000000000000

# Blockchain Configuration
# Private key for the game server wallet (required for score submissions)
PRIVATE_KEY=0x0000000000000000000000000000000000000000000000000000000000000000
```

### 3. Game Registration (Required)

Before the backend can submit scores, the game must be registered on the leaderboard contract:

```javascript
// This is done by the contract admin, not in code
await contract.registerGame(
  GAME_ADDRESS,     // Your game's address
  "Nad Racer",      // Game name
  "image_url",      // Game image URL
  "game_url"        // Game website URL
);
```

After registration, set the `GAME_ADDRESS` in your `.env` file.

### 4. Wallet Setup

The server needs a wallet with `GAME_ROLE` to submit scores:

1. Create a new wallet for the server
2. Fund it with some MON for gas fees
3. Have the contract admin grant it `GAME_ROLE`
4. Set the private key in `.env`

## API Endpoints

### Health Check
```http
GET /api/health
```

### Get Player Data
```http
GET /api/player/:playerAddress
```

### Submit Score
```http
POST /api/submit-score
Content-Type: application/json

{
  "playerAddress": "0x...",
  "score": 1250,
  "transactions": 1
}
```

### Development Notes
- The backend handles secure score submissions to blockchain
- Player data can be retrieved individually via player address
- All scores are accumulated on the Monad blockchain

## Running the Server

### Development
```bash
npm run dev
```

### Production
```bash
npm start
```

## Architecture

```
Frontend → Backend API → Monad Blockchain
    ↓         ↓             ↓
Display  Validate &   Store permanently
data     submit scores   onchain
```

**Note**: Leaderboards are handled directly by the frontend using the Monad Games API.

### Security Features

- **Server-side validation** - Prevents client-side score manipulation
- **Rate limiting** - 100 requests/15min, 10 score submissions/minute
- **Input validation** - Address format, score ranges, data types
- **CORS protection** - Only allows frontend origin
- **Helmet security** - Security headers

### Cost Structure

- **Reading data**: FREE (RPC calls)
- **Submitting scores**: Gas fees only (Monad network fees)
- **Storage**: FREE (onchain storage)

## Integration with Frontend

### Score Submissions
Update your frontend to submit scores through the backend:

```javascript
// Secure score submission through backend
const response = await fetch('/api/submit-score', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    playerAddress: userAddress,
    score: finalScore,
    transactions: 1
  })
});
```

### Player Data Retrieval
Fetch individual player data:

```javascript
// Get player statistics
const response = await fetch(`/api/player/${userAddress}`);
const playerData = await response.json();
// Returns: { gameScore, gameTransactions, totalScore }
```

### Leaderboards
Leaderboards are handled directly by the frontend using the Monad Games API.

## Development Notes

- The backend focuses solely on secure score submissions
- Player data is retrieved on-demand from the blockchain
- Monitor gas costs for score submissions
- All player tracking is handled by the Monad blockchain contract

## Contract Information

- **Contract Address**: `0xceCBFF203C8B6044F52CE23D914A1bfD997541A4`
- **Network**: Monad Testnet
- **Explorer**: https://testnet.monadexplorer.com

## Support

For issues with the leaderboard contract or game registration, contact the Monad team.