## Solana CLI Commands

### 1. Check Solana CLI Version

```sh
solana --version
```

📌 **Explanation**: Displays the currently installed Solana CLI version.

---

### 2. Configure Solana CLI

```sh
solana config set --url https://api.mainnet-beta.solana.com
```

📌 **Explanation**: Sets the default environment to connect to Solana Mainnet Beta. You can also switch to Devnet or Testnet:

```sh
solana config set --url https://api.devnet.solana.com
```

Check the current configuration:

```sh
solana config get
```

---

### 3. Generate a New Wallet

```sh
solana-keygen new --outfile ~/my-keypair.json
```

📌 **Explanation**: Creates a new keypair and saves it to `my-keypair.json`.

To display the public key of the generated keypair:

```sh
solana-keygen pubkey ~/my-keypair.json
```

---

### 4. Check Wallet Balance

```sh
solana balance
```

📌 **Explanation**: Displays the balance of the default wallet.

To check the balance of a specific wallet:

```sh
solana balance <PUBLIC_KEY>
```

---

### 5. Request Free SOL (Devnet or Testnet Only)

```sh
solana airdrop 1
```

📌 **Explanation**: Requests 1 SOL on Devnet/Testnet. This command does not work on Mainnet.

Request more SOL:

```sh
solana airdrop 5 <PUBLIC_KEY>
```

---

### 6. Transfer SOL to Another Address

```sh
solana transfer <RECIPIENT_ADDRESS> <AMOUNT_SOL>
```

📌 **Explanation**: Sends SOL from the default wallet to another address.

Example:

```sh
solana transfer 4k3DyjJw... 0.5 --allow-unfunded-recipient
```

---

### 7. Check Transaction History

```sh
solana transaction-history <PUBLIC_KEY>
```

📌 **Explanation**: Displays the transaction history of a wallet address.

---

### 8. Deploy a Smart Contract (Program)

```sh
solana program deploy <BPF_FILE_PATH>
```

📌 **Explanation**: Deploys a compiled BPF program to the blockchain.

Example:

```sh
solana program deploy ./dist/program/my_program.so
```

---

### 9. List Accounts Belonging to a Wallet

```sh
solana account <PUBLIC_KEY>
```

📌 **Explanation**: Displays detailed information about a Solana account, including balance, owner, etc.

---

### 10. Run a Validator Node (For Node Operators)

```sh
solana-validator --identity ~/validator-keypair.json --rpc-port 8899 --entrypoint entrypoint.mainnet-beta.solana.com:8001
```

📌 **Explanation**: Runs a validator node to participate in the Solana network.

---

### 11. Check Block Information

```sh
solana block <BLOCK_SLOT>
```

📌 **Explanation**: Displays details about a specific block on Solana.

---

### 12. Check Transaction Status

```sh
solana confirm <TRANSACTION_SIGNATURE>
```

📌 **Explanation**: Verifies the status of a transaction using its signature.

Example:

```sh
solana confirm 5H8vQ...as6
```

---

<!-- Copy Button Script for HTML Preview -->
<script>
document.addEventListener("DOMContentLoaded", function() {
    document.querySelectorAll("pre code").forEach((codeBlock) => {
        const button = document.createElement("button");
        button.className = "copy-button";
        button.innerText = "Copy";

        button.addEventListener("click", () => {
            navigator.clipboard.writeText(codeBlock.innerText).then(() => {
                button.innerText = "Copied!";
                setTimeout(() => {
                    button.innerText = "Copy";
                }, 2000);
            }).catch((err) => {
                console.error("Failed to copy: ", err);
            });
        });

        const pre = codeBlock.parentNode;
        pre.parentNode.insertBefore(button, pre);
    });
});
</script>

<style>
.copy-button {
    position: absolute;
    right: 10px;
    top: 10px;
    background: #007bff;
    color: white;
    border: none;
    padding: 5px 10px;
    font-size: 12px;
    cursor: pointer;
    border-radius: 4px;
}
.copy-button:hover {
    background: #0056b3;
}
pre {
    position: relative;
    background: #f5f5f5;
    padding: 10px;
    border-radius: 5px;
}
</style>
