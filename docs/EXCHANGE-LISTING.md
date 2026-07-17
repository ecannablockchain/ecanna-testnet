# Exchange / partner listing pack — E Canna Testnet

**Network:** E Canna Testnet · **Chain ID:** `4112` · **Symbol:** `tECNA`  
**GitHub (public source):** https://github.com/ecannablockchain/ecanna-testnet  

Use these links when an exchange or partner asks for testnet source, genesis, peers, and Geth build.

| What they ask | Link / value |
|---------------|----------------|
| **GitHub source** | https://github.com/ecannablockchain/ecanna-testnet |
| **genesis.json** | https://github.com/ecannablockchain/ecanna-testnet/blob/main/ecnachain/genesis.json |
| **static-nodes.json** (peer nodes) | https://github.com/ecannablockchain/ecanna-testnet/blob/main/ecnachain/static-nodes.json |
| **Raw genesis** | https://raw.githubusercontent.com/ecannablockchain/ecanna-testnet/main/ecnachain/genesis.json |
| **Raw static-nodes** | https://raw.githubusercontent.com/ecannablockchain/ecanna-testnet/main/ecnachain/static-nodes.json |
| **Docker / Geth image (compiled client)** | `ethereum/client-go:v1.13.15` — see `ecnachain/docker-compose.yml` |
| **Geth version (live)** | `1.13.15-stable` (commit `c5ba367e…`) |
| **Ubuntu (live production)** | **24.04 LTS** (also tested with **22.04 LTS** + Docker) |
| **Public RPC** | https://testnetrpc.ecnascan.com |
| **Explorer** | https://testnetexplorer.ecnascan.com |
| **API** | https://testnetapi.ecnascan.com |
| **Faucet** | https://testnetexplorer.ecnascan.com/faucet |
| **Website** | https://ecnascan.com |
| **Chainlist** | https://chainlist.org/?search=4112&testnets=true |
| **Genesis hash (block 0)** | `0x75a3446929625d15d01857be62f5ab10abde0ad01311a37664d4ccc27fbde3a6` |

> **Obsolete enode (do not use):** any peer ID starting with `9ad0e0…`. Always use GitHub `static-nodes.json`.

## Peer / bootnode (copy-paste)

```
enode://f762fd2f93af7d072aa497fab66e5e54800b9de96becd13b79378d2b89b6e567c6d703cf16a977e4463205b373c1b86b241c860a1d609405139f340938b96112@168.144.69.102:30313
```

- **P2P port:** `30313` TCP + UDP (mapped; does not conflict with mainnet `30303`)  
- **Host:** `168.144.69.102`  
- Place `static-nodes.json` under the node’s datadir `geth/` folder, or pass via bootnodes.
- Always use the enode from GitHub `static-nodes.json` (node ID can change after a wipe if not pinned).

## Node OS & client requirements

Same as mainnet: **Ubuntu 24.04 LTS** (live) or **22.04 LTS**, **Geth v1.13.15-stable**, `amd64`, Docker optional, EVM **london** (no Shanghai — stock Geth Clique), sync `full` + `gcmode archive`.  
See [`docs/EXCHANGE-LISTING.md`](./EXCHANGE-LISTING.md) for the full table.

## Geth start command (sync-only full node)

```bash
geth \
  --datadir ./data \
  --networkid 4112 \
  --syncmode full \
  --gcmode archive \
  --http \
  --http.addr "127.0.0.1" \
  --http.port "8545" \
  --http.api "eth,net,web3,txpool" \
  --ws \
  --ws.addr "127.0.0.1" \
  --ws.port "8546" \
  --ws.api "eth,net,web3" \
  --port 30313 \
  --discovery.port 30313 \
  --nat any
```

Public RPC for testnet wallets: **https://testnetrpc.ecnascan.com**. Do **not** expose `debug` / `admin` / `db` on a public HTTP listener.

## How to sync a testnet full node (short)

1. Run Geth **v1.13.15** on **Ubuntu 22.04/24.04** (or Docker image above).  
2. `geth init --datadir ./data` with the raw genesis.  
3. Copy `static-nodes.json` into `./data/geth/static-nodes.json`.  
4. Start with networkid **4112**, P2P open to peer on **30313**.  

## Mainnet companion

https://github.com/ecannablockchain/ecanna-mainnet (chain ID **4111** / ECNA) · [`docs/EXCHANGE-LISTING.md`](./EXCHANGE-LISTING.md)

## Do not send exchanges

Private keys, miner/faucet hex, SSH passwords, SQL credentials, or server `.env` files.
