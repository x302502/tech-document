<script>
function copyToClipboard(elementId) {
    var copyText = document.getElementById(elementId);
    navigator.clipboard.writeText(copyText.innerText).then(() => {
        alert("Copied to clipboard!");
    }).catch(err => {
        console.error("Failed to copy: ", err);
    });
}
</script>

## Solana CLI Commands

### 1. Check Solana CLI Version
<button onclick="copyToClipboard('code1')">Copy</button>
<pre id="code1">
solana --version
</pre>
📌 **Explanation**: Displays the currently installed Solana CLI version.

---

### 2. Configure Solana CLI
<button onclick="copyToClipboard('code2')">Copy</button>
<pre id="code2">
solana config set --url https://api.mainnet-beta.solana.com
</pre>
📌 **Explanation**: Sets the default environment to connect to Solana Mainnet Beta. You can also switch to Devnet or Testnet:
<button onclick="copyToClipboard('code3')">Copy</button>
<pre id="code3">
solana config set --url https://api.devnet.solana.com
</pre>

Check the current configuration:
<button onclick="copyToClipboard('code4')">Copy</button>
<pre id="code4">
solana config get
</pre>

---

### 3. Generate a New Wallet
<button onclick="copyToClipboard('code5')">Copy</button>
<pre id="code5">
solana-keygen new --outfile ~/my-keypair.json
</pre>
📌 **Explanation**: Creates a new keypair and saves it to `my-keypair.json`.

To display the public key of the generated keypair:
<button onclick="copyToClipboard('code6')">Copy</button>
<pre id="code6">
solana-keygen pubkey ~/my-keypair.json
</pre>

---

### 4. Check Wallet Balance
<button onclick="copyToClipboard('code7')">Copy</button>
<pre id="code7">
solana balance
</pre>
📌 **Explanation**: Displays the balance of the default wallet.

To check the balance of a specific wallet:
<button onclick="copyToClipboard('code8')">Copy</button>
<pre id="code8">
solana balance <PUBLIC_KEY>
</pre>

---

### 5. Request Free SOL (Devnet or Testnet Only)
<button onclick="copyToClipboard('code9')">Copy</button>
<pre id="code9">
solana airdrop 1
</pre>
📌 **Explanation**: Requests 1 SOL on Devnet/Testnet. This command does not work on Mainnet.

Request more SOL:
<button onclick="copyToClipboard('code10')">Copy</button>
<pre id="code10">
solana airdrop 5 <PUBLIC_KEY>
</pre>

---

### 6. Transfer SOL to Another Address
<button onclick="copyToClipboard('code11')">Copy</button>
<pre id="code11">
solana transfer <RECIPIENT_ADDRESS> <AMOUNT_SOL>
</pre>
📌 **Explanation**: Sends SOL from the default wallet to another address.

Example:
<button onclick="copyToClipboard('code12')">Copy</button>
<pre id="code12">
solana transfer 4k3DyjJw... 0.5 --allow-unfunded-recipient
</pre>

---

### 7. Check Transaction History
<button onclick="copyToClipboard('code13')">Copy</button>
<pre id="code13">
solana transaction-history <PUBLIC_KEY>
</pre>
📌 **Explanation**: Displays the transaction history of a wallet address.

---

### 8. Deploy a Smart Contract (Program)
<button onclick="copyToClipboard('code14')">Copy</button>
<pre id="code14">
solana program deploy <BPF_FILE_PATH>
</pre>
📌 **Explanation**: Deploys a compiled BPF program to the blockchain.

Example:
<button onclick="copyToClipboard('code15')">Copy</button>
<pre id="code15">
solana program deploy ./dist/program/my_program.so
</pre>

---

### 9. List Accounts Belonging to a Wallet
<button onclick="copyToClipboard('code16')">Copy</button>
<pre id="code16">
solana account <PUBLIC_KEY>
</pre>
📌 **Explanation**: Displays detailed information about a Solana account, including balance, owner, etc.

---

### 10. Run a Validator Node (For Node Operators)
<button onclick="copyToClipboard('code17')">Copy</button>
<pre id="code17">
solana-validator --identity ~/validator-keypair.json --rpc-port 8899 --entrypoint entrypoint.mainnet-beta.solana.com:8001
</pre>
📌 **Explanation**: Runs a validator node to participate in the Solana network.

---

### 11. Check Block Information
<button onclick="copyToClipboard('code18')">Copy</button>
<pre id="code18">
solana block <BLOCK_SLOT>
</pre>
📌 **Explanation**: Displays details about a specific block on Solana.

---

### 12. Check Transaction Status
<button onclick="copyToClipboard('code19')">Copy</button>
<pre id="code19">
solana confirm <TRANSACTION_SIGNATURE>
</pre>
📌 **Explanation**: Verifies the status of a transaction using its signature.

Example:
<button onclick="copyToClipboard('code20')">Copy</button>
<pre id="code20">
solana confirm 5H8vQ...as6
</pre>
