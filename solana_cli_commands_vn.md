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

## Lệnh Solana CLI

### 1. Kiểm tra phiên bản Solana CLI

<pre><code>
solana --version
</code></pre>

📌 **Giải thích**: Hiển thị phiên bản Solana CLI hiện tại.

---

### 2. Cấu hình Solana CLI

<pre><code>
solana config set --url https://api.mainnet-beta.solana.com
</code></pre>

📌 **Giải thích**: Đặt môi trường mặc định để kết nối với Mainnet Beta của Solana. Bạn cũng có thể chuyển sang Devnet hoặc Testnet:

<pre><code>
solana config set --url https://api.devnet.solana.com
</code></pre>

Kiểm tra cấu hình hiện tại:

<pre><code>
solana config get
</code></pre>

---

### 3. Tạo ví mới

<pre><code>
solana-keygen new --outfile ~/my-keypair.json
</code></pre>

📌 **Giải thích**: Tạo một keypair mới và lưu vào file `my-keypair.json`.

Để hiển thị địa chỉ ví của keypair:

<pre><code>
solana-keygen pubkey ~/my-keypair.json
</code></pre>

---

### 4. Kiểm tra số dư ví

<pre><code>
solana balance
</code></pre>

📌 **Giải thích**: Hiển thị số dư của ví mặc định.

Kiểm tra số dư của một ví cụ thể:

<pre><code>
solana balance &lt;PUBLIC_KEY&gt;
</code></pre>

---

### 5. Nhận SOL miễn phí (chỉ trên Devnet hoặc Testnet)

<pre><code>
solana airdrop 1
</code></pre>

📌 **Giải thích**: Yêu cầu 1 SOL trên Devnet/Testnet. Nếu dùng Mainnet, lệnh này không hoạt động.

Yêu cầu nhiều SOL hơn:

<pre><code>
solana airdrop 5 &lt;PUBLIC_KEY&gt;
</code></pre>

---

### 6. Gửi SOL đến một địa chỉ khác

<pre><code>
solana transfer &lt;ĐỊA_CHỈ_NGƯỜI_NHẬN&gt; &lt;SỐ_LƯỢNG_SOL&gt;
</code></pre>

📌 **Giải thích**: Chuyển SOL từ ví mặc định đến một địa chỉ khác.

Ví dụ:

<pre><code>
solana transfer 4k3DyjJw... 0.5 --allow-unfunded-recipient
</code></pre>

---

### 7. Kiểm tra lịch sử giao dịch

<pre><code>
solana transaction-history &lt;PUBLIC_KEY&gt;
</code></pre>

📌 **Giải thích**: Xem lịch sử giao dịch của một địa chỉ ví.

---

### 8. Triển khai Smart Contract (Program)

<pre><code>
solana program deploy &lt;ĐƯỜNG_DẪN_TỚI_TỆP_BPF&gt;
</code></pre>

📌 **Giải thích**: Triển khai một chương trình đã biên dịch (BPF) lên blockchain.

Ví dụ:

<pre><code>
solana program deploy ./dist/program/my_program.so
</code></pre>

---

### 9. Kiểm tra danh sách các tài khoản thuộc ví

<pre><code>
solana account &lt;PUBLIC_KEY&gt;
</code></pre>

📌 **Giải thích**: Hiển thị thông tin chi tiết về tài khoản Solana, bao gồm số dư, owner, v.v.

---

### 10. Chạy Validator Node (chỉ dành cho node operator)

<pre><code>
solana-validator --identity ~/validator-keypair.json --rpc-port 8899 --entrypoint entrypoint.mainnet-beta.solana.com:8001
</code></pre>

📌 **Giải thích**: Chạy một validator node để tham gia mạng lưới Solana.

---

### 11. Kiểm tra thông tin về một Block

<pre><code>
solana block &lt;BLOCK_SLOT&gt;
</code></pre>

📌 **Giải thích**: Xem thông tin về một block trên Solana.

---

### 12. Kiểm tra trạng thái của một giao dịch

<pre><code>
solana confirm &lt;TRANSACTION_SIGNATURE&gt;
</code></pre>

📌 **Giải thích**: Kiểm tra trạng thái giao dịch bằng Transaction Signature.

Ví dụ:

<pre><code>
solana confirm 5H8vQ...as6
</code></pre>
