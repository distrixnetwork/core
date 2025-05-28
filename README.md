**Distrix Chain**
*Layer-1 Proof-of-Work Blockchain • Ethash • 2,000+ TPS • 100% EVM Compatible*

---

## 📖 Overview

Distrix is a high-performance, Ethash-based proof-of-work blockchain designed for large-scale decentralized applications. With over 2,000 transactions per second and full Ethereum Virtual Machine compatibility, Distrix enables seamless smart-contract deployment, while its decentralized compute marketplace unlocks new opportunities for distributed computing incentives.

Key features:

* **Consensus:** Ethash PoW
* **Throughput:** >2,000 TPS
* **EVM Compatibility:** 100% (smart contracts, tooling)
* **Network ID:** 23333
* **Decentralized Compute Marketplace**

---

## 🚀 Quickstart: Running a Distrix Node

Follow these steps to spin up your own Distrix node and join the network.

### 1. Prerequisites

* Linux (Ubuntu 18.04+ recommended)
* [Distrix (geth)](https://github.com/distrixnetwork/core/releases/tag/v0.0.1) v0.0.1
* ≥4 GB RAM, SSD storage
* Open ports: `30309` (P2P)

---

### 2. Clone the Repository

```bash
git clone https://github.com/distrixnetwork/core.git
cd core
make geth
```

---

### 3. Initialize the Chain

Initialize your data directory with the genesis block:

```bash
./geth --datadir node/ init genesis.json
```

* **`--datadir node/`**: directory for chain data
* **`genesis.json`**: network’s initial state (located in repo root folder)

---

### 4. Configure and Run Your Node

Use the following command to start syncing, mining, and exposing RPC endpoints:

```bash
./geth \
  --nousb \
  --datadir ./node/$(pwd) \
  --syncmode "full" \
  --port 30311 \
  --miner.gasprice 0 \
  --http \
  --http.addr "0.0.0.0" \
  --http.port 8547 \
  --http.api admin,eth,miner,net,txpool,personal,web3 \
  --authrpc.port 8552 \
  --allow-insecure-unlock \
  --unlock <YOUR_MINER_ADDRESS> \
  --password password.txt \
  --miner.etherbase <YOUR_MINER_ADDRESS> \
  --ipcpath "geth.ipc" \
  --identity "Distrix Node Solo" \
  --networkid 23333 \
  --miner.extradata "Distrix-Solo" \
  --bootnodes "enode://dcb1a016870b9b18c03dc1b0c30713c2b00dbfc1d2a2f5785b756b9a23052caddb5aa3eb7201dab18788ac5e6489906e2a779ef44b559b848271230d417c04ae@142.93.247.184:30309,enode://a48c52e54d1640596d08f6a1cebbb26fb192e1f52b5134b690bb7a163cbd9636367fd53146d45e519e0b1c64d3e22dab715b8aac27ef272820b2716e982ea9b3@147.182.139.117:30309,enode://9698958a75870295fa3d630813a3a0ad05679d79a18e04fd16deb5312ffac2943a7bd0b4ed681f67a3df2d5961478dd47478a80bb4a9b2c16185d052bb8cff49@142.93.247.184:30372" \
  > geth_output.log 2>&1 &
```

**Flags explained:**

* `--syncmode "full"`: full chain validation
* `--miner.gasprice 0`: zero-gas-price mining for testnets
* `--http` & `--http.api`: enable and expose JSON-RPC APIs
* `--allow-insecure-unlock`: unlock accounts via RPC (testnet only)
* `--unlock` & `--password`: miner address and password file
* `--miner.etherbase`: mining rewards recipient
* `--identity`: node name shown in peering
* `--networkid`: Distrix network identifier
* `--miner.extradata`: extra data field (“Distrix-Solo”)
* `--bootnodes`: comma-separated list of bootnode enode URLs
* `> geth_output.log 2>&1 &`: run in background, log output

---

### 5. Bootnode Configuration

Distrix’s bootnodes ensure your node can discover and connect to peers:

```text
enode://dcb1a016870b9b18c03dc1b0c30713c2b00dbfc1d2a2f5785b756b9a23052caddb5aa3eb7201dab18788ac5e6489906e2a779ef44b559b848271230d417c04ae@142.93.247.184:30309
enode://a48c52e54d1640596d08f6a1cebbb26fb192e1f52b5134b690bb7a163cbd9636367fd53146d45e519e0b1c64d3e22dab715b8aac27ef272820b2716e982ea9b3@147.182.139.117:30309
enode://9698958a75870295fa3d630813a3a0ad05679d79a18e04fd16deb5312ffac2943a7bd0b4ed681f67a3df2d5961478dd47478a80bb4a9b2c16185d052bb8cff49@142.93.247.184:30372
```

You can override or add additional bootnodes via the `--bootnodes` flag as demonstrated above.

---

## 🔧 Common Commands

* **Check Sync Status**

  ```bash
  ./geth attach ./node/geth.ipc --exec "eth.syncing"
  ```
* **List Peers**

  ```bash
  ./geth attach ./node/geth.ipc --exec "admin.peers"
  ```
* **View Miner Stats**

  ```bash
  ./geth attach ./node/geth.ipc --exec "miner.hashrate"
  ```

---

## 🛠️ Troubleshooting

* **Stuck at Block X:**

  * Ensure your `bootnodes` are reachable (ping IPs).
  * Check that ports (30309, 8547) are open in your firewall.

* **Account Unlock Fails:**

  * Verify `password.txt` contains the correct passphrase.
  * Confirm the address matches an account in `node/keystore/`.

* **Low Peer Count:**

  * Double-check network connectivity.
  * Add more bootnodes or seed peers manually.

---

## 📚 Further Resources

* **Distrix Documentation:** [docs.distrix.network](https://docs.distrix.network)
* **Community & Support:**

  * Fourm: [discord.distrix.network](https://forum.distrix.network/)
  * Telegram: [t.me/distrixchain](https://t.me/DistrixChain)

---

