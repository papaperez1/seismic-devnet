# ````````````````````Seismic-Devnet Contract Deployment `````````````

![image](https://github.com/user-attachments/assets/5a8b48f5-4992-4bc8-8047-4d3ec484c14d)

Seismic is an L1 blockchain capable of encrypting arbitrary smart contracts. Deploying a single Solidity contract is sufficient to launch an encrypted DeFi protocol, no custom infrastructure required.

We achieved this by restructuring the modern blockchain stack around TEEs. This involved forking key components such as Solidity, Reth, and Foundry. By doing so, we were able to fully leverage the confidentiality guarantees of secure enclaves and eliminate the need for additional infrastructure.

This is not incetivized.

## System requirement
Any OS with 10 GB disk space is sufficient. Below commands are for Linux.

## Install pre-requisites

1. Install Rust
   
```
curl https://sh.rustup.rs -sSf | sh  # choose default, just press enter
. "$HOME/.cargo/env"
```

2. Install jq

```
apt install jq
```

3. Install chalk

```
npm install chalk
```

4. Install sfoundryup

```
curl -L \
     -H "Accept: application/vnd.github.v3.raw" \
     "https://api.github.com/repos/SeismicSystems/seismic-foundry/contents/sfoundryup/install?ref=seismic" | bash
source ~/.bashrc
```

5. Run sfoundryup

```
sfoundryup  # takes between 5m to 60m, and stalling for a while at 98% normal
```

6. Install foundry

```
curl -L https://foundry.paradigm.xyz/ | bash && source ~/.bashrc && foundryup
```
## Deploy an encrypted contract
### Clone Seismic Repo

```
git clone --recurse-submodules https://github.com/SeismicSystems/try-devnet.git
cd try-devnet/packages/contract/ && sed -i 's/\bscast\b/cast/g' ../common/wallet.sh
```

### Deploy contract

```
bash script/deploy.sh
```

## Interact with an encrypted contract
### Install Bun

```
Install Bun
```

### Install node dependencies

```
cd ..
cd cli && bun install
```

### Send Transaction

```
bash script/transact.sh
```
![image](https://github.com/user-attachments/assets/53357676-f0da-426a-9f3a-f569dbf20253)

DONE!!!
