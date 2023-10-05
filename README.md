# Relayer

Relayer is a tool designed to communicate with blockchain network through transactions. Whenher you're deploying smart contracts, deposit or withdraw tokens, funding account. Relayer simplifies the process of sending transaction to blockhain.

## Table of Contents

- [Relayer](#relayer)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Configuring and using Relayer](#configuring-and-using-relayer)
  - [Contributing](#contributing)
  - [License](#license)


## Introduction

Transaction refers to a contract, agreement or transfer. Blockchain transaction is nothing but data transmission across the network of computers in a blockchain system. Relayer simplifies the process of data transmission through the network, making it a useful tool for VM developers and enthusiasts.
.

## Prerequisites

Before using Relayer, make sure you have the following prerequisites:

- Go: Event Tracker is built with Go, so you'll need it installed on your system. You can download it from [go.dev](https://go.dev/doc/install).

## Installation

Relayer is just a library, and is currently not intended to be used as a standalone application. You can use it by referencing the latest commit on `main` branch, and then start the relayer as a part of your application.

## Usage

Relayer can be used to deploy smart contracts, fund accounts or data transmission through blockchain network.

### Configuring and using Relayer

You can configure Relayer to specify public node URL,  as well as the rest of the configuration parameters. 

```go
  func WithClient(client *jsonrpc.Client) TxRelayerOption {
	return func(t *TxRelayerImpl) {
		t.client = client
	  }
  }

func WithIPAddress(ipAddress string) TxRelayerOption {
	return func(t *TxRelayerImpl) {
		t.ipAddress = ipAddress
	}
}

func WithReceiptTimeout(receiptTimeout time.Duration) TxRelayerOption {
	return func(t *TxRelayerImpl) {
		t.receiptTimeout = receiptTimeout
	}
}

func WithWriter(writer io.Writer) TxRelayerOption {
	return func(t *TxRelayerImpl) {
		t.writer = writer
	}
}

  txrelayer.NewTxRelayer(
    txrelayer.WithIPAddress(wp.JSONRPCAddr)
    ,txrelayer.WithReceiptTimeout(150*time.Milisecond)
    ,...)
```
Our recommendations are:
- `SendTransaction` - signs given transaction by provided key and sends it to the blockchain
- `Call` - executes a message call immediately without creating a transaction on the blockchain
- `Client` - returns jsonrpc client
- `SendTransactionLocal` - sends non-signed transaction (this function is meant only for testing purposes and is about to be removed at some point)
- `ConvertTxnToCallMsg` - converts txn instance to call message

## Contributing
We welcome contributions to Event Tracker! If you have ideas for improvements or find bugs, please open an issue or submit a pull request.

## License
Event Tracker is licensed under the MIT License.


