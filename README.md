# Ethereum_NFT

## Background 
Exploration of Ethereum NFT data using Python, SQL and ML concepts.

## Data Source
* Source data nfts.sqlite - not uploaded due to file size.

This is a sample data set retrieved from [Kaggle](https://www.kaggle.com/simiotic/ethereum-nfts).

* This dataset represents the activity of the Ethereum non-fungible token (NFT) market between the following dates:

    * Start date: April 1, 2021
    * End date: September 25, 2021

These data were collected using [Moonstream.to](https://moonstream.to/) as part of Moonstream's open data efforts.

The dataset is based on on-chain NFT Transfer events as its core. There are several derived tables which make the data convenient to analyze.

### Data Schema
* Contracts, tokens, and events

A non-fungible token is a digital asset representing a distinct idea or physical object.

On the Ethereum blockchain, these tokens are created using Ethereum smart contracts which represent entire collections of non-fungible tokens. The most famous examples of such contracts are CryptoPunks and CryptoKitties.

Every time an NFT is transferred on the Ethereum blockchain, it emits a Transfer event which is stored on the blockchain. This dataset was constructed by crawling the emitted Transfer events that were emitted in the period of time represented by the dataset.

* Core relations

The core relations in this dataset are:

    1. 'mints' - events from the Ethereum blockchain indicating the creation of a new NFT.
    2. 'transfers' - events from the Ethereum blockchain indicating a transfer of ownership of a previously minted NFT.

* Columns:

'event_id' - a unique ID associated with each event, generated when we created the dataset
'transaction_hash' - the hash of the Ethereum transaction in which we observed the event
'block_number' - the number of the Ethereum transaction block in which the transaction containing the event was mined
'nft_address' - the address of the smart contract containing the NFT that the event describes
'token_id' - the identifier that represents the NFT that the event describes within the context of the smart contract with address nft_address
'from_address' - the address that owned the NFT before the Transfer event denoted by this row in the relation (it is not the address that initiated the transaction in which the NFT transfer took place)
'to_address' - the address that owned the NFT after the Transfer event denoted by this row in the relation (it is not the address that was the recipient the transaction in which the NFT transfer took place)
'transaction_value' - the amount of WEI that were sent with the transaction in which the Transfer event took place
'timestamp' - the Unix timestamp at which the Ethereum transaction block with number block_number was mined into the Ethereum blockchain

* Derived relations
For ease of analysis, several derived relations were included in this dataset:

'current_market_values' - the current (estimated) market value of each NFT, in WEI
'current_owners' - the current owner of each NFT
'nfts' - available metadata (from Moonstream) about the NFT contracts represented in the dataset
'transfer_statistics_by_address' - transfers in and out of every address that was involved in an NFT transfer
'transfer_values_quartile_10_distribution_per_address' and 'transfer_values_quantile_25_distribution_per_address' - for each 10th or 4th quantile of each NFT collection, these relations give the proportion of the value of the most valuable token in that collection that the quantile represents

## Data Cleaning & Wrangling
* Utilized two methods: python and SQL for demonstration of effort in both programming languages.

* To be continued.

---

## Technical Elements

* N/A


## Reference
* Data is from [Kaggle](https://www.kaggle.com/simiotic/ethereum-nfts), whch was donated by [Moonstream.to](https://moonstream.to/).

* Check out the Moonstream team that collected the data and their [github page](https://github.com/bugout-dev/moonstream).