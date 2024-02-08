# Mint and Transfer ckTESTBTC with Testnet Bitcoin

**Requirements**

Before you start this tutorial ensure you have Plug or Bitfinity Wallet  Extenstions installed in your Wallet.

![Screenshot from 2024-02-08 05-17-57](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/3a58f8f1-5cb8-4bba-814c-8c44a2823b27)
![Screenshot from 2024-02-08 05-21-34](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/78459579-ec87-44d5-8601-eeca48b7930f)

You should also have Electrum Wallet [installed.To](http://installed.To) install it click here:https://electrum.org/

Once successfully installed in your pc you can launch the Testnet wallet by running this command:

```
python3 Electrum-4.4.6/run_electrum --testnet
```

It should look like this so input the password of the testnet wallet you created.

![Screenshot from 2024-02-08 05-30-15](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/ee406340-0e93-447e-be2f-4f815e15a570)


1. **Obtain Testnet Bitcoin (BTC):** 
    - Create a Bitcoin Testnet wallet using services like [Bitpay](https://bitpay.com/) or [Electrum](https://electrum.org/). Make sure to note down your Testnet Bitcoin wallet address.For our tutorial we will use Electrum.
    - Request Testnet Bitcoin from a [Bitcoin Testnet Faucet](https://www.datawallet.com/crypto/get-bitcoin-testnet-tokens) and send it to your Testnet address.
    - Use https://coinfaucet.eu/en/btc-testnet/ or https://bitcoinfaucet.uo1.net/ to get yourself some tokens.
    - **Take a screenshot** of your Testnet Bitcoin transaction confirmation or balance in your wallet.Please note that the test bitcoins might take up to 80 confirmations for them to be fully in your testnet wallet.
        
   ![Screenshot from 2024-02-08 02-59-44](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/bee3f65d-799b-476c-8558-8e25544bca7f)

![Screenshot from 2024-02-08 05-40-03](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/e6cae943-ae0b-4da1-a955-632b169c355f)

![Screenshot from 2024-02-08 05-43-03](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/72d2bb61-dd73-481a-b382-ee3822b8e0df)

1. **Clone the IC Repository and Prepare for Minting ckTESTBTC:**
    - Clone the IC repository:
        
        ```
        git clone https://github.com/dfinity/ic.git
        ```
        
    - Change to the ckBTC/Testnet directory:
        
        ```
        cd ic/rs/bitcoin/ckbtc/testnet/
        ```
        
      ![Screenshot from 2024-02-08 05-48-58](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/f462efbe-a245-435f-ad4d-2852636fbcb2)

        
        - From this directory, you can run the commands as outlined in the [“Bitcoin to ckBTC” section of the README](https://github.com/dfinity/ic/tree/master/rs/bitcoin/ckbtc/minter#bitcoin-to-ckbtc)
2. **Obtain the Deposit Address of the ckTESTBTC Minter:**
    - Run the following command to get the deposit address:
        
        ```
        dfx canister --network ic call minter get_btc_address "(record {subaccount=null;})"
        ```
        
        - You may need to install version 0.12.1 of DFX. Use this command to install: `DFX_VERSION=0.12.1 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"`)
        - Ensure you have a **`.pem`** file to run the command. **In most cases, this file is generated automatically, so you can proceed as usual.** However, if you encounter an error message stating that the **`.pem`** file is missing, you'll need to regenerate the identity. If the original file is lost and not backed up, it cannot be recreated exactly as it was.
    - **Take a screenshot** of the deposit address you received from the ckbtc minter.
        
       ![Screenshot from 2024-02-08 05-53-55](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/47dd5584-ae53-47ba-b286-ba3163aac0f3)

        
3. **Send Testnet Bitcoin to the Deposit Address Provided by the Minter:**
    - Using the wallet interface, send Testnet Bitcoin to the Deposit Address Provided by the Minter.
        - The minimum retrieval amount is 5,000 Satoshis. This amount is sufficient to cover the fees for the transactions we create. Note that it can be challenging to obtain more than 10,000 Satoshis on the BTC testnet.100 million Satoshis is equivalent to 1BTC.
        - 5,000 Satoshis is equivalent to 0.00005 BTC.
    - After completing the transaction, **take a screenshot** of the explorer displaying the outcome of your transaction.

 ![Screenshot from 2024-02-08 05-57-49](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/02e720c2-6ad4-4d77-b006-34ee00bcf68a)
![Screenshot from 2024-02-08 05-58-40](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/f4884343-1079-4e02-ad51-465e6ac4c459)
![Screenshot from 2024-02-08 05-59-05](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/e35bc272-9178-4c66-a708-985486ace36c)
![Screenshot from 2024-02-08 05-59-18](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/e5394d5a-3289-4856-a4c9-6c4728884595)

        
4. **Notify the Minter About the Transfer:**
    - Use the following command to update the balance:
        
        ```
        dfx canister --network ic call minter update_balance "(record {subaccount=null;})"
        ```
        
        - The ckTESTBTC waits for **3 confirmations**, so you have to wait some time between sending the testbtc and calling “update_balance”.
    - **Take a screenshot** showing ckTESTBTC has been minted successfully.
        
    ![Screenshot from 2024-02-08 06-46-38](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/be4b7fcb-11f7-40e4-ac96-ecc733a832aa)

        
5. **Transfer ckBTC to Your Wallet:**
    - Copy the principal of your wallet (e.g. [Plug](https://plugwallet.ooo/), [Stoic](https://www.stoicwallet.com/) or Bitfinity Wallet) and replace **`<PRINCIPAL>`** in the following command, adjusting **`<AMOUNT>`** to the desired amount (in Satoshis):
        
        ```
        dfx canister --network ic call ledger icrc1_transfer "(record { to = record { owner = principal \"<PRINCIPAL>\" }; amount = <AMOUNT>; })"
        ```
        
        - Obtain your principal using: **`dfx identity get-principal`**.
        - Remember, the amount should be specified in 10^-8 ckTESTBTC (i.e., the equivalent of Satoshis).
      ![Screenshot from 2024-02-08 06-56-58](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/cbf49e4b-1bad-463b-8e39-5cb18fbca869)  
     ![Screenshot from 2024-02-08 07-04-18](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/917c39f5-ca24-40a0-8438-2d64512c622c)

        
    - Import the ckTESTBTC token into your wallet. To do this, use “import token,” select “custom,” and enter the ledger canister ID “mc6ru-gyaaa-aaaar-qaaaq-cai” with “ICRC1” as the token standard.
    - **Take a screenshot** that displays your wallet balance, confirming the successful completion of the ckTESTBTC transfer.
        
        
    
    For plug wallet here is the output:
    

![Screenshot from 2024-02-08 07-10-25](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/fc9c989d-76c1-451d-b8bb-c8fca1807146)
![Screenshot from 2024-02-08 07-11-37](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/08bbb390-f1f6-466d-9695-852bff0dd4b4)
![Screenshot from 2024-02-08 07-12-40](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/ac85f633-24d7-497d-8315-5f26f989cc06)


For Bitfinity Wallet it will look like this:

![Screenshot from 2024-02-08 07-17-36](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/29016756-1267-458e-b6d3-7eaabb00a51c)
![Screenshot from 2024-02-08 07-22-08](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/c3327ec3-1e91-41f1-9696-f738a7a3867d)
![Screenshot from 2024-02-08 07-22-45](https://github.com/Kushite-ICP-HUb-East-Africa/Introduction-to-ckBTC-Token/assets/81568615/2dd46280-5a2a-41cd-a0a1-b4ecdac6c3cd)


### Submission:

- **Screenshots**: Submit screenshots of
    
    1) Your Testnet Bitcoin balance in your wallet (Step 1).
    2) The deposit address you received (Step 3).
    3) The explorer displaying the outcome of your transaction from your Testnet Bitcoin wallet to the minter (Step 4).
    4) A confirmation showing that ckTESTBTC has been minted successfully (Step 5).
    5) A confirmation of the ckTESTBTC transfer from the ledger canister to your wallet (Step 6).
    

### You can submit your answers to Tevin.