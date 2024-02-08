# Mint and Transfer ckTESTBTC with Testnet Bitcoin

1. **Obtain Testnet Bitcoin (BTC):** 
    - Create a Bitcoin Testnet wallet using services like [Bitpay](https://bitpay.com/) or [Electrum](https://electrum.org/). Make sure to note down your Testnet Bitcoin wallet address.
    - Request Testnet Bitcoin from a [Bitcoin Testnet Faucet](https://www.datawallet.com/crypto/get-bitcoin-testnet-tokens) and send it to your Testnet address.
    - Use https://coinfaucet.eu/en/btc-testnet/ or https://bitcoinfaucet.uo1.net/ to get yourself some tokens.
    - **Take a screenshot** of your Testnet Bitcoin transaction confirmation or balance in your wallet.
        
        ![Example) Testnet Bitcoin transaction confirmation](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/f8900bdb-4fff-423f-ac69-cc55111208f6/Untitled.png)
        
        Example) Testnet Bitcoin transaction confirmation
        
2. **Clone the IC Repository and Prepare for Minting ckTESTBTC:**
    - Clone the IC repository:
        
        ```
        git clone https://github.com/dfinity/ic.git
        ```
        
    - Change to the ckBTC/Testnet directory:
        
        ```
        cd ic/rs/bitcoin/ckbtc/testnet/
        ```
        
        - From this directory, you can run the commands as outlined in the [“Bitcoin to ckBTC” section of the README](https://github.com/dfinity/ic/tree/master/rs/bitcoin/ckbtc/minter#bitcoin-to-ckbtc)
3. **Obtain the Deposit Address of the ckTESTBTC Minter:**
    - Run the following command to get the deposit address:
        
        ```
        dfx canister --network ic call minter get_btc_address "(record {subaccount=null;})"
        ```
        
        - You may need to install version 0.12.1 of DFX. Use this command to install: `DFX_VERSION=0.12.1 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"`)
        - Ensure you have a **`.pem`** file to run the command. **In most cases, this file is generated automatically, so you can proceed as usual.** However, if you encounter an error message stating that the **`.pem`** file is missing, you'll need to regenerate the identity. If the original file is lost and not backed up, it cannot be recreated exactly as it was.
    - **Take a screenshot** of the deposit address you received.
        
        ![Example) Minter deposit address](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/eeddd33b-8d0f-4291-8854-44bac9ae3fec/Untitled.png)
        
        Example) Minter deposit address
        
4. **Send Testnet Bitcoin to the Deposit Address Provided by the Minter:**
    - Using the wallet interface, send Testnet Bitcoin to the Deposit Address Provided by the Minter.
        - The minimum retrieval amount is 5,000 Satoshis. This amount is sufficient to cover the fees for the transactions we create. Note that it can be challenging to obtain more than 10,000 Satoshis on the BTC testnet.
        - 5,000 Satoshis is equivalent to 0.00005 BTC.
    - After completing the transaction, **take a screenshot** of the explorer displaying the outcome of your transaction.
        
        ![Example) Testnet Bitcoin wallet → Minter](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/aa590618-cb17-4b46-8ebf-3204651f73a2/Untitled.png)
        
        Example) Testnet Bitcoin wallet → Minter
        
5. **Notify the Minter About the Transfer:**
    - Use the following command to update the balance:
        
        ```
        dfx canister --network ic call minter update_balance "(record {subaccount=null;})"
        ```
        
        - The ckTESTBTC waits for 3 confirmations, so you have to wait some time between sending the testbtc and calling “update_balance”.
    - **Take a screenshot** showing ckTESTBTC has been minted successfully.
        
        ![Example) ckTESTBTC is minted!](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/5fdae0d8-eefc-490f-a74b-e4fa1c414c89/Untitled.png)
        
        Example) ckTESTBTC is minted!
        
6. **Transfer ckBTC to Your Wallet:**
    - Copy the principal of your wallet (e.g. [Plug](https://plugwallet.ooo/), [Stoic](https://www.stoicwallet.com/)) and replace **`<PRINCIPAL>`** in the following command, adjusting **`<AMOUNT>`** to the desired amount (in Satoshis):
        
        ```
        dfx canister --network ic call ledger icrc1_transfer "(record { to = record { owner = principal \"<PRINCIPAL>\" }; amount = <AMOUNT>; })"
        ```
        
        - Obtain your principal using: **`dfx identity get-principal`**.
        - Remember, the amount should be specified in 10^-8 ckTESTBTC (i.e., the equivalent of Satoshis).
    - Import the ckTESTBTC token into your wallet. To do this, use “import token,” select “custom,” and enter the ledger canister ID “mc6ru-gyaaa-aaaar-qaaaq-cai” with “ICRC1” as the token standard.
    - **Take a screenshot** that displays your wallet balance, confirming the successful completion of the ckTESTBTC transfer.
        
        ![Example) Plug wallet interface showing ckTESTBTC balance](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/83da3b9a-6404-45c2-beb5-416147721c0f/Untitled.png)
        
        Example) Plug wallet interface showing ckTESTBTC balance
        

### Submission:

- **Screenshots**: Submit screenshots of
    
    1) Your Testnet Bitcoin balance in your wallet (Step 1).
    2) The deposit address you received (Step 3).
    3) The explorer displaying the outcome of your transaction from your Testnet Bitcoin wallet to the minter (Step 4).
    4) A confirmation showing that ckTESTBTC has been minted successfully (Step 5).
    5) A confirmation of the ckTESTBTC transfer from the ledger canister to your wallet (Step 6).
    

### You can submit your answers to Tevin or Steve.