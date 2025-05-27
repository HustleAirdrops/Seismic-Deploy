# Seismic Foundry & Devnet Setup Guide

This guide will help you set up the Seismic Foundry environment, deploy a contract, and interact with it using encrypted transactions.

---

## 1. Install Rust

```sh
curl https://sh.rustup.rs -sSf | sh
. "$HOME/.cargo/env"
```

---

## 2. Install Dependencies

```sh
sudo apt update
sudo apt install -y jq file
```

---

## 3. Install `sfoundryup`

```sh
curl -L \
    -H "Accept: application/vnd.github.v3.raw" \
    "https://api.github.com/repos/SeismicSystems/seismic-foundry/contents/sfoundryup/install?ref=seismic" | bash
source ~/.bashrc
sfoundryup
```

---

## 4. Clone Repositories

```sh
git clone --recurse-submodules https://github.com/SeismicSystems/try-devnet.git
cd try-devnet/packages/contract/
git clone https://github.com/SeismicSystems/seismic-foundry.git
```

---

## 5. Build `cast` Tool

```sh
cd seismic-foundry
cargo build --release -p cast
cp target/release/scast ~/.seismic/bin/
echo 'export PATH="$HOME/.seismic/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
cd ..
```

---

## 6. Deploy the Contract

```sh
bash script/deploy.sh
```
- This script will generate a wallet and display a Faucet URL and wallet address.
- Use the Faucet URL to fund your wallet.

---

## 7. Interact with the Encrypted Contract

### a. Go to Home Directory

```sh
cd ~
```

### b. Install Bun

```sh
curl -fsSL https://bun.sh/install | bash
```

### c. Install Node Dependencies

```sh
cd try-devnet/packages/cli/
source ~/.bashrc
bun install
```

### d. Send Transactions

```sh
bash script/transact.sh
```

---

**You're all set!**  
Follow the prompts in each step and refer to the official documentation for troubleshooting.
