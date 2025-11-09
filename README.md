# Bitcoin-Block-Transaction-Scraper
This Python script automatically fetches Bitcoin transaction IDs (txids) from public blockchain explorer APIs, starting from a specific block height and continuing up to a defined end block. It’s designed for reliable, long-term data collection — it automatically switches APIs if one fails or gets rate-limited.
🧱 Bitcoin Block Transaction Scraper

This Python script automatically fetches Bitcoin transaction IDs (txids) from public blockchain explorer APIs, starting from a specific block height and continuing up to a defined end block.
It’s designed for reliable, long-term data collection — it automatically switches APIs if one fails or gets rate-limited.

🚀 Features

Automatic API switching
The script tests multiple public APIs (Blockchair, Blockchain.info, Blockstream, Mempool.space) and automatically uses the first one that responds correctly.
If the current API fails several times, it switches to another.

Persistent progress tracking
The last successfully processed block height is saved in last_block.txt, so the script can resume from where it left off after interruption.

Transaction ID collection
Every transaction hash (txid) from each processed block is saved line-by-line to txids.txt.

Fail-safe error handling
Handles network errors, invalid responses, and rate limits (HTTP 429) gracefully without crashing.

Randomized user-agents
Each request uses a random browser user-agent string to reduce the risk of being rate-limited by API providers.

⚙️ How It Works

Reads the last processed block height from last_block.txt (or starts from DEFAULT_START_BLOCK if none exists).

Iterates through block heights up to the target END_BLOCK.

For each block:

Checks which API is working and fetches the block data.

Extracts all transaction IDs (txids).

Saves them to txids.txt.

Updates the last processed block number.

If 3 consecutive blocks fail to load, the script automatically switches to another available API.

📂 Files
File	Description
main.py	Main script that runs the fetcher
last_block.txt	Stores the last successfully processed block height
txids.txt	Contains all collected transaction IDs
🧰 Configuration

Edit these constants at the bottom of the script:

DEFAULT_START_BLOCK = 1     # Starting block (use your own)
END_BLOCK = 400000          # Last block to process


You can restart the script anytime — it will resume from the block saved in last_block.txt.

📦 Requirements
pip install requests

🧠 Example Output
▶️ Start fetching from block 1000 to 1050.
📦 Fetching transactions for block 1000...
✅ Found 1523 transactions in block 1000.
📦 Fetching transactions for block 1001...
⚠️ No transactions or API error for block 1001.
🔁 Too many errors — switching API...
...
🎯 Found 75243 total transactions.

🛡️ Use Cases

Building datasets of historical Bitcoin transaction IDs

Blockchain analytics and data research

Monitoring transaction patterns or block sizes

Collecting TXIDs for later use in forensic or verification scripts

🧑‍💻 Author Notes

This script was created for educational and data-collection purposes — it does not perform any mining or private key access.
It’s safe to run, read-only, and uses only public blockchain APIs.
BTC donation address:
bc1q4nyq7kr4nwq6zw35pg0zl0k9jmdmtmadlfvqhr
