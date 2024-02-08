# Mint and Transfer ckTESTBTC with Testnet Bitcoin

**Requirements**

Before you start this tutorial ensure you have Plug or Bitfinity Wallet  Extenstions installed in your Wallet.

![Screenshot from 2024-02-08 05-17-57.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/6468c136-22ff-4ff3-a9cc-8fb638ffde34/Screenshot_from_2024-02-08_05-17-57.png)

![Screenshot from 2024-02-08 05-21-34.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/4f426c15-d478-409c-b866-acd3bacb5e1d/Screenshot_from_2024-02-08_05-21-34.png)

You should also have Electrum Wallet [installed.To](http://installed.To) install it click here:https://electrum.org/

Once successfully installed in your pc you can launch the Testnet wallet by running this command:

```
python3 Electrum-4.4.6/run_electrum --testnet
```

It should look like this so input the password of the testnet wallet you created.

![Screenshot from 2024-02-08 05-30-15.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/f1230071-380c-4769-b16f-45c9b2edef86/Screenshot_from_2024-02-08_05-30-15.png)

1. **Obtain Testnet Bitcoin (BTC):** 
    - Create a Bitcoin Testnet wallet using services like [Bitpay](https://bitpay.com/) or [Electrum](https://electrum.org/). Make sure to note down your Testnet Bitcoin wallet address.For our tutorial we will use Electrum.
    - Request Testnet Bitcoin from a [Bitcoin Testnet Faucet](https://www.datawallet.com/crypto/get-bitcoin-testnet-tokens) and send it to your Testnet address.
    - Use https://coinfaucet.eu/en/btc-testnet/ or https://bitcoinfaucet.uo1.net/ to get yourself some tokens.
    - **Take a screenshot** of your Testnet Bitcoin transaction confirmation or balance in your wallet.Please note that the test bitcoins might take up to 80 confirmations for them to be fully in your testnet wallet.
        
        ![Screenshot from 2024-02-08 02-59-44.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/f1356e18-f68e-495b-93f0-86eb2d7ccad0/Screenshot_from_2024-02-08_02-59-44.png)
        
    
    ![Screenshot from 2024-02-08 05-40-03.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/fed5dfdf-a55b-4247-90be-e421c13d5188/Screenshot_from_2024-02-08_05-40-03.png)
    

![Screenshot from 2024-02-08 05-43-03.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/8bdc5612-6f33-4f4d-a7c8-2e3c0d3296fe/Screenshot_from_2024-02-08_05-43-03.png)

1. **Clone the IC Repository and Prepare for Minting ckTESTBTC:**
    - Clone the IC repository:
        
        ```
        git clone https://github.com/dfinity/ic.git
        ```
        
    - Change to the ckBTC/Testnet directory:
        
        ```
        cd ic/rs/bitcoin/ckbtc/testnet/
        ```
        
        ![Screenshot from 2024-02-08 05-48-58.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/b928de58-6b28-45f5-b30b-c709f6af66e2/Screenshot_from_2024-02-08_05-48-58.png)
        
        - From this directory, you can run the commands as outlined in the [“Bitcoin to ckBTC” section of the README](https://github.com/dfinity/ic/tree/master/rs/bitcoin/ckbtc/minter#bitcoin-to-ckbtc)
2. **Obtain the Deposit Address of the ckTESTBTC Minter:**
    - Run the following command to get the deposit address:
        
        ```
        dfx canister --network ic call minter get_btc_address "(record {subaccount=null;})"
        ```
        
        - You may need to install version 0.12.1 of DFX. Use this command to install: `DFX_VERSION=0.12.1 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"`)
        - Ensure you have a **`.pem`** file to run the command. **In most cases, this file is generated automatically, so you can proceed as usual.** However, if you encounter an error message stating that the **`.pem`** file is missing, you'll need to regenerate the identity. If the original file is lost and not backed up, it cannot be recreated exactly as it was.
    - **Take a screenshot** of the deposit address you received from the ckbtc minter.
        
        ![Screenshot from 2024-02-08 05-53-55.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/02bef9e9-697a-4951-a9fb-839038611732/Screenshot_from_2024-02-08_05-53-55.png)
        
3. **Send Testnet Bitcoin to the Deposit Address Provided by the Minter:**
    - Using the wallet interface, send Testnet Bitcoin to the Deposit Address Provided by the Minter.
        - The minimum retrieval amount is 5,000 Satoshis. This amount is sufficient to cover the fees for the transactions we create. Note that it can be challenging to obtain more than 10,000 Satoshis on the BTC testnet.100 million Satoshis is equivalent to 1BTC.
        - 5,000 Satoshis is equivalent to 0.00005 BTC.
    - After completing the transaction, **take a screenshot** of the explorer displaying the outcome of your transaction.
        
        ![Screenshot from 2024-02-08 05-57-49.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/b8e8b766-2079-4329-9a70-891a43d9150a/Screenshot_from_2024-02-08_05-57-49.png)
        
        ![Screenshot from 2024-02-08 05-58-40.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/92479a2b-e85f-4217-bdd7-43e27f65f885/Screenshot_from_2024-02-08_05-58-40.png)
        
        ![Screenshot from 2024-02-08 05-59-05.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/262987dc-2f9f-4a4d-b3c0-f376d56c793a/Screenshot_from_2024-02-08_05-59-05.png)
        
        ![Screenshot from 2024-02-08 05-59-18.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/985b340a-de65-488a-b519-2ef6ad4de7a0/Screenshot_from_2024-02-08_05-59-18.png)
        
4. **Notify the Minter About the Transfer:**
    - Use the following command to update the balance:
        
        ```
        dfx canister --network ic call minter update_balance "(record {subaccount=null;})"
        ```
        
        - The ckTESTBTC waits for **3 confirmations**, so you have to wait some time between sending the testbtc and calling “update_balance”.
    - **Take a screenshot** showing ckTESTBTC has been minted successfully.
        
        ![Screenshot from 2024-02-08 06-46-38.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/47acf88a-a172-4698-898b-91e86c3ffaa1/Screenshot_from_2024-02-08_06-46-38.png)
        
5. **Transfer ckBTC to Your Wallet:**
    - Copy the principal of your wallet (e.g. [Plug](https://plugwallet.ooo/), [Stoic](https://www.stoicwallet.com/) or Bitfinity Wallet) and replace **`<PRINCIPAL>`** in the following command, adjusting **`<AMOUNT>`** to the desired amount (in Satoshis):
        
        ```
        dfx canister --network ic call ledger icrc1_transfer "(record { to = record { owner = principal \"<PRINCIPAL>\" }; amount = <AMOUNT>; })"
        ```
        
        - Obtain your principal using: **`dfx identity get-principal`**.
        - Remember, the amount should be specified in 10^-8 ckTESTBTC (i.e., the equivalent of Satoshis).
        
        ![Screenshot from 2024-02-08 07-04-18.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/9222243d-9829-447f-a9d6-1a6db49ebf19/Screenshot_from_2024-02-08_07-04-18.png)
        
    - Import the ckTESTBTC token into your wallet. To do this, use “import token,” select “custom,” and enter the ledger canister ID “mc6ru-gyaaa-aaaar-qaaaq-cai” with “ICRC1” as the token standard.
    - **Take a screenshot** that displays your wallet balance, confirming the successful completion of the ckTESTBTC transfer.
        
        
    
    For plug wallet here is the output:
    

![Screenshot from 2024-02-08 07-10-25.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/9f6f26a0-b0d5-4e6b-9720-3b09bb7437dd/Screenshot_from_2024-02-08_07-10-25.png)

![Screenshot from 2024-02-08 07-11-37.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/fa99bf71-e662-4cea-b3b9-d620d5d08b52/Screenshot_from_2024-02-08_07-11-37.png)

![Screenshot from 2024-02-08 07-12-40.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/db3da41b-08d8-473b-bcf5-f04fbc233593/Screenshot_from_2024-02-08_07-12-40.png)

![Screenshot from 2024-02-08 07-17-36.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/64e0cf44-f7d5-4dac-91d9-9981ea561c31/Screenshot_from_2024-02-08_07-17-36.png)

For Bitfinity Wallet it will look like this:

![Screenshot from 2024-02-08 07-17-36.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/e552fe96-ef71-4f80-8a40-45446b2345b1/Screenshot_from_2024-02-08_07-17-36.png)

![Screenshot from 2024-02-08 07-22-08.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/a39981fd-fe61-46c2-9f2e-1fc0582d1bb6/Screenshot_from_2024-02-08_07-22-08.png)

![Screenshot from 2024-02-08 07-22-45.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c449c26a-1935-47bd-809e-51dbfecd9cca/9ebda295-b804-4ac1-a486-8c4ab0638a37/Screenshot_from_2024-02-08_07-22-45.png)

### Submission:

- **Screenshots**: Submit screenshots of
    
    1) Your Testnet Bitcoin balance in your wallet (Step 1).
    2) The deposit address you received (Step 3).
    3) The explorer displaying the outcome of your transaction from your Testnet Bitcoin wallet to the minter (Step 4).
    4) A confirmation showing that ckTESTBTC has been minted successfully (Step 5).
    5) A confirmation of the ckTESTBTC transfer from the ledger canister to your wallet (Step 6).
    

### You can submit your answers to Tevin.