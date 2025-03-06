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

## Solana CLI Commands

### 1. Check Solana CLI Version

<pre><code>
solana --version
</code></pre>

📌 **Explanation**: Displays the currently installed Solana CLI version.

---

### 2. Configure Solana CLI

<pre><code>
solana config set --url https://api.mainnet-beta.solana.com
</code></pre>

📌 **Explanation**: Sets the default environment to connect to Solana Mainnet Beta. You can also switch to Devnet or Testnet:

<pre><code>
solana config set --url https://api.devnet.solana.com
</code></pre>

Check the current configuration:

<pre><code>
solana config get
</code></pre>

---

### 3. Generate a New Wallet

<pre><code>
solana-keygen new --outfile ~/my-keypair.json
</code></pre>

📌 **Explanation**: Creates a new keypair and saves it to `my-keypair.json`.

To display the public key of the generated keypair:

<pre><code>
solana-keygen pubkey ~/my-keypair.json
</code></pre>

---

### 4. Check Wallet Balance

<pre><code>
solana balance
</code></pre>

📌 **Explanation**: Displays the balance of the default wallet.

To check the balance of a specific wallet:

<pre><code>
solana balance &lt;PUBLIC_KEY&gt;
</code></pre>

---

### 5. Request Free SOL (Devnet or Testnet Only)

<pre><code>
solana airdrop 1
</code></pre>

📌 **Explanation**: Requests 1 SOL on Devnet/Testnet. This command does not work on Mainnet.

Request more SOL:

<pre><code>
solana airdrop 5 &lt;PUBLIC_KEY&gt;
</code></pre>

---

### 6. Transfer SOL to Another Address

<pre><code>
solana transfer &lt;RECIPIENT_ADDRESS&gt; &lt;AMOUNT_SOL&gt;
</code></pre>

📌 **Explanation**: Sends SOL from the default wallet to another address.

Example:

<pre><code>
solana transfer 4k3DyjJw... 0.5 --allow-unfunded-recipient
</code></pre>

---

### 7. Check Transaction History

<pre><code>
solana transaction-history &lt;PUBLIC_KEY&gt;
</code></pre>

📌 **Explanation**: Displays the transaction history of a wallet address.

---

### 8. Deploy a Smart Contract (Program)

<pre><code>
solana program deploy &lt;BPF_FILE_PATH&gt;
</code></pre>

📌 **Explanation**: Deploys a compiled BPF program to the blockchain.

Example:

<pre><code>
solana program deploy ./dist/program/my_program.so
</code></pre>

---

### 9. List Accounts Belonging to a Wallet

<pre><code>
solana account &lt;PUBLIC_KEY&gt;
</code></pre>

📌 **Explanation**: Displays detailed information about a Solana account, including balance, owner, etc.

---

### 10. Run a Validator Node (For Node Operators)

<pre><code>
solana-validator --identity ~/validator-keypair.json --rpc-port 8899 --entrypoint entrypoint.mainnet-beta.solana.com:8001
</code></pre>

📌 **Explanation**: Runs a validator node to participate in the Solana network.

---

### 11. Check Block Information

<pre><code>
solana block &lt;BLOCK_SLOT&gt;
</code></pre>

📌 **Explanation**: Displays details about a specific block on Solana.

---

### 12. Check Transaction Status

<pre><code>
solana confirm &lt;TRANSACTION_SIGNATURE&gt;
</code></pre>

📌 **Explanation**: Verifies the status of a transaction using its signature.

Example:

<pre><code>
solana confirm 5H8vQ...as6
</code></pre>
