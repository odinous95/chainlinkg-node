
---

````markdown
# Chainlink Node with Docker

This guide explains how to run a Chainlink node using Docker and connect it to an Ethereum-compatible EVM node.

## Prerequisites

- [Docker](https://www.docker.com/get-started) installed on your system.
- Access to an Ethereum EVM node (e.g., via [Infura](https://infura.io/), [Alchemy](https://www.alchemy.com/), or your own local node).

## 1. Pull the Chainlink Docker Image

```bash
docker pull smartcontract/chainlink:latest
````

## 2. Create a Configuration File

Create a file named `config.env` in your working directory with the following content:

```env
ETH_URL=https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID
ETH_CHAIN_ID=1
API_PORT=6688
LOG_LEVEL=debug
```

> ⚠️ Replace `YOUR_INFURA_PROJECT_ID` with your actual project ID from Infura or your own Ethereum node URL.
> ⚠️ Use the appropriate `ETH_CHAIN_ID` (e.g., `1` for Mainnet, `11155111` for Sepolia, `5` for Goerli, etc.).

## 3. Run the Chainlink Node Container

```bash
docker run -p 6688:6688 --env-file=config.env smartcontract/chainlink
```

* `-p 6688:6688`: Exposes the Chainlink API on port 6688.
* `--env-file=config.env`: Loads your environment configuration.

## 4. Access the Chainlink Dashboard

Open your browser and go to:

```
http://localhost:6688
```

If you're running on a remote server, replace `localhost` with your server's IP address.

## 5. Ethereum Node Requirements

Ensure your Ethereum node:

* Is fully synced.
* Supports HTTP/WS endpoints.
* Allows read/write access for smart contract interactions.

Example EVM node services:

* [Infura](https://infura.io/)
* [Alchemy](https://alchemy.com/)
* [QuickNode](https://www.quicknode.com/)

---

## Troubleshooting

* Make sure your Ethereum node URL is correct and accessible.
* Check logs using `docker logs <container_id>` if the node doesn't start.
* Ensure ports are open if deploying on a remote machine.

## Resources

* [Official Chainlink Documentation](https://docs.chain.link/)
* [Chainlink GitHub](https://github.com/smartcontractkit/chainlink)

---
