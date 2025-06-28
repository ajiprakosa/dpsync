# Daftar Properti Sync (dpsync)

This folder contains tools and scripts for synchronizing property listings between the blockchain and MongoDB.

## Structure

- `synchronizer.ts`  
  Script for fetching missed listings from the blockchain and storing them in MongoDB.
- `.github/workflows/`  
  Contains GitHub Actions workflows for CI/CD and scheduled sync jobs.

## Usage

### Environment Variables

Set the following environment variables (in your shell, `.env`, or CI/CD settings):

- `MONGO_URI` – MongoDB connection string
- `DB_DATABASE` – MongoDB database name
- `COLLECTION_NAME` – MongoDB collection name for listings
- `DP_CONTRACT_ADDRESS` – Blockchain contract address
- `BLOCKCHAIN_PROVIDER_URL` – Blockchain provider URL
- `DP_ABI_VERSION` – ABI version for the contract

### Running the Synchronizer

#### TypeScript Script

```bash
# Install dependencies
npm install

# Build (if needed)
tsc synchronizer.ts

# Run the script
node synchronizer.js
```

### GitHub Actions

- The workflow in `.github/workflows/sync.yml` runs the synchronizer on a schedule or manually.
- Most configuration is provided via repository/environment variables or secrets.

## Notes

- The synchronizer will connect to both MongoDB and the blockchain, and keep listings in sync.
- Make sure your environment variables are set correctly before running.
- For production, ensure `NODE_ENV=production` is set.

---