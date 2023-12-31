# Bitex

<div align="center">
  <img src="https://btc.cryptoid.info/logo/btc.png" width="100px" />
</div>
<br />

The **Bitex** Python module provides an easy and convenient way to interact with blockchain data using the blockchain explorer. Whether you're interested in querying cryptocurrency addresses, retrieving balances, exploring transactions, or getting detailed information about blocks, Bitex has you covered.

## Installation

To install the **Bitex** module, you can use the following `pip` command:

```bash
pip install bitex-blockchain-explorer
```

## Usage

Import the **bitex** module and follow these steps to interact with blockchain data:

```python
import bitex

# Define the cryptocurrency address
address = '1FeexV6bAHb8ybZjqQMjJrcCrHGW9sb6uF'

# Initialize the Bitex blockchain explorer
blockchain = bitex.Bitex()

# Search for the address on different chains
chains = blockchain.search(address)

# Choose a chain (e.g., 'btc') for further operations
chain = 'btc'

# Get the balance for the selected address
balance = blockchain.balance(chain, address)

# Convert the balance from satoshi to BTC format
balance_btc = blockchain.format_balance(balance['confirmed'])
print(f'Balance: {balance_btc:.8f} {chain.upper()}')

# Retrieve a limited number of transactions for the address
limit = 3
transactions = blockchain.transactions(chain, address, limit=limit)

# Access transaction details
if transactions:
    example_transaction = transactions[2]  # Get the third transaction
    txid = example_transaction.txid
    block = example_transaction.block
    block_height = block.height
    block_position = block.position

    # Get more details about the transaction
    transaction_details = example_transaction.details()

    # Extract specific details
    transaction_txid = transaction_details.txid
    transaction_size = transaction_details.size
    # ... (other details)

    # Get transaction details as a dictionary
    transaction_details_dict = transaction_details.get()

# Note: Replace 'your_crypto_address_here' with your actual cryptocurrency address
```

## Features

- Search for addresses on different chains.
- Retrieve balance information for a given address.
- Convert balance from satoshi to BTC format.
- Get transaction details and block information.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
