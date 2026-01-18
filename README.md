# BoxMeOut - Prediction Market Platform

A blockchain-based prediction market platform built on Stellar/Soroban, enabling users to create, predict, and trade on sports outcomes.

## Project Structure

```
boxmeout_stella/
├── backend/                  # Node.js/Express API
│   ├── src/
│   │   ├── routes/          # API endpoints
│   │   ├── controllers/     # Business logic
│   │   ├── services/        # Service layer
│   │   ├── database/        # Database models
│   │   ├── websocket/       # Real-time updates
│   │   └── utils/           # Utilities
│   └── .env.example         # Environment template
│
├── contracts/               # Soroban Smart Contracts (Rust)
│   ├── contracts/boxmeout/
│   │   ├── src/
│   │   │   ├── factory.rs   # Market factory
│   │   │   ├── market.rs    # Market logic
│   │   │   ├── amm.rs       # Automated Market Maker
│   │   │   ├── treasury.rs  # Fee management
│   │   │   ├── oracle.rs    # Price oracle
│   │   │   └── lib.rs       # Module exports
│   │   └── tests/           # Test suite
│   └── Cargo.toml           # Workspace config
│
└── frontend/                # React + Vite UI
    ├── src/
    │   ├── components/      # React components
    │   ├── data/            # Mock data
    │   └── main.jsx         # Entry point
    ├── public/              # Static assets
    └── vite.config.js       # Vite configuration
```

## Tech Stack

**Blockchain:**
- Stellar Network (testnet/mainnet)
- Soroban WASM Smart Contracts (Rust)
- Account-based model with persistent storage

**Backend:**
- Node.js + Express
- PostgreSQL + MongoDB + Redis
- Socket.io for real-time updates
- Stellar.js SDK

**Frontend:**
- React 18+
- Vite
- TailwindCSS (recommended)

## Smart Contracts

### Architecture

5 Modular Contracts:

1. **Factory** - Market creation and registry
2. **Market** - Individual prediction logic
3. **AMM** - Automated Market Maker with CPMM pricing
4. **Treasury** - Fee collection and distribution
5. **Oracle** - Multi-source consensus for resolution

### TIER 1 Status: ✅ COMPLETE

All initialization functions implemented:
- Factory.initialize()
- Treasury.initialize()
- Oracle.initialize()
- Oracle.register_oracle()
- Market.initialize()
- AMM.initialize()

### Next Steps: TIER 2 (Market Creation)

- [ ] Factory.create_market()
- [ ] AMM.create_pool()

## Development

### Prerequisites

```bash
# Rust + Soroban
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install stellar-cli

# Node.js
node >= 18
npm >= 9

# Stellar Test Account
# Get testnet account: https://laboratory.stellar.org/
```

### Setup Backend

```bash
cd backend
npm install
cp .env.example .env
# Configure your environment variables
npm start
```

### Setup Contracts

```bash
cd contracts/contracts/boxmeout
cargo build --release --target wasm32-unknown-unknown
```

### Setup Frontend

```bash
cd frontend
npm install
npm run dev
```

## Documentation

- [PROJECT_DOCUMENTATION.md](/docs/PROJECT_DOCUMENTATION.md) - Platform overview
- [TECHNICAL_ARCHITECTURE.md](/docs/TECHNICAL_ARCHITECTURE.md) - Backend architecture
- [SMART_CONTRACT_ARCHITECTURE.md](/docs/SMART_CONTRACT_ARCHITECTURE.md) - Contract design
- [TESTING_GUIDE.md](/docs/TESTING_GUIDE.md) - Testing standards
- [GITHUB_ISSUES.md](/docs/GITHUB_ISSUES.md) - TIER 2 & 3 roadmap

## Testing

```bash
# Run all contract tests
cd contracts/contracts/boxmeout
cargo test

# Run specific test file
cargo test --test factory_test

# View test output
cargo test -- --nocapture
```

## Deployment

### Contract Deployment (Stellar Testnet)

1. Build contracts individually
2. Deploy to Stellar using Stellar CLI
3. Call initialize() on each contract
4. Store contract addresses

### Backend Deployment

```bash
# Configure production .env
npm run build
npm start
```

## Project Timeline

**Week 1:** ✅ TIER 1 - Initialization (Complete)
**Week 2:** 🔄 TIER 2 - Market Creation (In Progress)
**Week 3:** ⏳ TIER 3 - User Trading
**Week 4:** ⏳ TIER 4 - Market Resolution
**Week 5:** ⏳ TIER 5 - Treasury & Analytics

## Key Features

- **Prediction Markets** - Create markets for any outcome
- **Commit-Reveal** - Privacy-preserving predictions
- **AMM Trading** - CPMM-based dynamic pricing
- **Multi-Oracle** - 2-of-3 consensus for resolution
- **Fee System** - Platform (8%) + Leaderboard (2%) + Creator (0.5-1%)
- **Leaderboard** - Track top traders
- **Real-Time** - WebSocket updates for odds and trades

## Contributing

1. Create feature branch
2. Implement with tests
3. Ensure all tests pass
4. Submit PR with description

## License

MIT License

## Contact

Built with ❤️ for Stellar Network prediction markets
