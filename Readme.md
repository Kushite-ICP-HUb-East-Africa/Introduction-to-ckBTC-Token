## ckBTC
![ckBTC-token-1](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/a56b5e5c-aba3-40f5-8fb3-5d0d68a4781e)

ckBTC — a multi-chain bitcoin twin, trustlessly created by chain-key cryptography and Internet Computer smart contracts that directly hold raw bitcoin. Send and receive ckBTC with 1-2 second finality and negligible fees.
Chain-key Bitcoin (ckBTC) is an ICRC-2-compliant token that is backed 1:1 by bitcoins held 100% on the mainnet.

Hold, send and receive native bitcoin as if the Internet Computer and the Bitcoin network were one blockchain. No bridges or off-chain intermediaries.
# Features of ckbtc
* Fast TXs with negligible fees
Enables small and casual transactions with bitcoin.

Fixed transaction fee: 10 satoshis
Finality: 1-2 sec
Full balance always available. No channel liquidity issues

* Programable bitcoin
Build applications that address real world needs.

Canister smart contracts can hold and send ckBTC
Build web applications with BTC support. Users only need a browser

* Transactions across multiple chains
Send and receive ckBTC value to and from addresses on either network

No centralized custodians or bridges
Chain-key integrations with other networks like Ethereum


In 2021, El Salvador became the first country in the world to use Bitcoin as legal tender. However, as bitcoin transactions are slow and have high fees, they are not practical for daily economic activities such as buying groceries or getting a coffee.

The Bitcoin network integration on the Internet Computer is extremely powerful in terms of security and interoperability, but every bitcoin transaction still suffers the same low throughput, high latency, and high fees native to the Bitcoin network. Recent surge in popularity of Bitcoin Ordinals and BRC-20 tokens resulted in Bitcoin's network to be highly congested. This pushed transaction fees above $30, rendering casual every-day transactions completely impractical.

Chain-key Bitcoin (ckBTC), a multi-chain bitcoin twin on ICP introduces layer 2 functionality fuelled by ICP properties like speed, scalability and low transaction fees to bitcoin. ckBTC helps reduce the load on the Bitcoin network, while making every-day bitcoin transactions feasible, which realizes a key part of Satoshi's original vision.

ckBTC implements ICRC-1, the fungible token standard on the Internet Computer, and can be integrated easily by any Web3 service running on ICP.

The ckBTC functionality is provided through an interplay of two canisters:

* The ckBTC minter.
* The ckBTC ledger.

The ckBTC ledger is responsible for keeping account balances and for transferring ckBTC between accounts. It provides the following functionality:

Enables the ckBTC minter to mint and burn ckBTC.
Facilitates the transfer of ckBTC among users.
The ckBTC minter is responsible for the minting and burning of ckBTC tokens. It uses the following workflow:

Tokens are minted when a user transfers bitcoins to a specific Bitcoin address under the ckBTC minter's control. The Bitcoin address uniquely identifies the owner of the sent bitcoins.
The ckBTC minter waits for confirmations of all Bitcoin transactions that affect the total supply of ckBTC (because of the lack of finality in Bitcoin).
For Bitcoin retrieval requests, the ckBTC minter burns ckBTC before transferring the corresponding BTC amount (minus fees) using a regular Bitcoin transaction.

  A detailed description of the ckBTC minter can be found in here:
  https://github.com/dfinity/ic/tree/master/rs/bitcoin/ckbtc/minter

# Why it’s not a bridged token.
The key innovations behind ckBTC are the native Bitcoin integration and chain-key ECDSA signing — advanced threshold cryptography integrated with ICP. In short, chain-key ECDSA is a set of cryptographic protocols that allow Internet Computer nodes to cooperatively create ECDSA signatures, which can be used to sign bitcoin transactions, using a highly fault-tolerant, decentralized network that is resilient to attacks by malicious nodes. The secret key is never stored in one place, instead it is broken down into key shares held by ICP nodes that are re-shared periodically. When requested, nodes use their key shares to collectively sign BTC transactions without recreating the original secret key.

This enables a pair of canister smart contracts to trustlessly create ckBTC, a multichain bitcoin twin that can be controlled by smart contracts and sent with near instant finality for negligible fees — all without the need for bridges or centralized custodians.

This is important, because blockchain bridges are centralized, insecure, cumbersome and costly. The insecurity alone is a dealbreaker: between 2021-2022, more than 2 billion dollars was stolen by exploiting blockchain bridges.

The recent incident where the FTX exchange acted as the custodian, and Sollet the bridge for wrapping and unwrapping BTC and ETH on Solana, demonstrates how bridges and intermediaries can act as single points of failures and are highly vulnerable to hacks. Ethereum smart contracts behind a bridge make asset transfers between blockchains possible, but users must still trust a third-party centralized custodian to manage the digital assets whose code is often not publicly verifiable.

# Why it’s not a wrapped token
More than a token, while ckBTC implements the ICRC-1 fungible token standard, the pair of canister smart contracts also allow bitcoin to be freely sent between addresses either on the Bitcoin network or the Internet Computer, making it the fir

# How ckBTC's security was assessed
Several security assessments are taken on critical components of the Internet Computer such as ckBTC to ensure robust security. These include TLA+ models to formally verify some guarantees, several internal and external security assessments. In 2023, both Bitcoin integration and ckBTC have undergone an external security audit conducted by Trail of Bits with no severe issues found.

# How it differs from Lightning
The Lightning Network is the most well known Layer-2 for Bitcoin. Like ckBTC, it allows fast and cheap transfers of BTC value off the Bitcoin blockchain.

Unlike Lightning, ckBTC does not require peer-to-peer payment channels to be established and funded. This means that your full ckBTC balance can always be transferred — no network liquidity limitations.

Canister smart contracts can programmatically hold and transfer ckBTC, making it possible to develop fully on-chain Layer-2 applications for Bitcoin, which is not possible using the Lightning Network.

Another key difference is that ckBTC transaction fees are fixed, and not dependent on the transaction amount, variable intermediate forwarding, or unexpected channel funding fees.

In the future, ckBTC will be available on other networks like Ethereum – also directly, and without bridges, thanks to chain-key cryptography integrations.