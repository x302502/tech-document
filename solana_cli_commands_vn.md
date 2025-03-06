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

## Lệnh Solana CLI

### 1. Kiểm tra phiên bản Solana CLI

<button onclick="copyToClipboard('code1')">Copy</button>

<pre id="code1">
solana --version
</pre>

📌 **Giải thích**: Hiển thị phiên bản Solana CLI hiện tại.

---

### 2. Cấu hình Solana CLI

<button onclick="copyToClipboard('code2')">Copy</button>

<pre id="code2">
solana config set --url https://api.mainnet-beta.solana.com
</pre>

📌 **Giải thích**: Đặt môi trường mặc định để kết nối với Mainnet Beta của Solana. Bạn cũng có thể chuyển sang Devnet hoặc Testnet:
<button onclick="copyToClipboard('code3')">Copy</button>

<pre id="code3">
solana config set --url https://api.devnet.solana.com
</pre>

Kiểm tra cấu hình hiện tại:
<button onclick="copyToClipboard('code4')">Copy</button>

<pre id="code4">
solana config get
</pre>

---

### 3. Tạo ví mới

<button onclick="copyToClipboard('code5')">Copy</button>

<pre id="code5">
solana-keygen new --outfile ~/my-keypair.json
</pre>

📌 **Giải thích**: Tạo một keypair mới và lưu vào file `my-keypair.json`.

Để hiển thị địa chỉ ví của keypair:
<button onclick="copyToClipboard('code6')">Copy</button>

<pre id="code6">
solana-keygen pubkey ~/my-keypair.json
</pre>

---

### 4. Kiểm tra số dư ví

<button onclick="copyToClipboard('code7')">Copy</button>

<pre id="code7">
solana balance
</pre>

📌 **Giải thích**: Hiển thị số dư của ví mặc định.

Kiểm tra số dư của một ví cụ thể:
<button onclick="copyToClipboard('code8')">Copy</button>

<pre id="code8">
solana balance <PUBLIC_KEY>
</pre>

---

### 5. Nhận SOL miễn phí (chỉ trên Devnet hoặc Testnet)

<button onclick="copyToClipboard('code9')">Copy</button>

<pre id="code9">
solana airdrop 1
</pre>

📌 **Giải thích**: Yêu cầu 1 SOL trên Devnet/Testnet. Nếu dùng Mainnet, lệnh này không hoạt động.

Yêu cầu nhiều SOL hơn:
<button onclick="copyToClipboard('code10')">Copy</button>

<pre id="code10">
solana airdrop 5 <PUBLIC_KEY>
</pre>

---

### 6. Gửi SOL đến một địa chỉ khác

<button onclick="copyToClipboard('code11')">Copy</button>

<pre id="code11">
solana transfer <ĐỊA_CHỈ_NGƯỜI_NHẬN> <SỐ_LƯỢNG_SOL>
</pre>

📌 **Giải thích**: Chuyển SOL từ ví mặc định đến một địa chỉ khác.

Ví dụ:
<button onclick="copyToClipboard('code12')">Copy</button>

<pre id="code12">
solana transfer 4k3DyjJw... 0.5 --allow-unfunded-recipient
</pre>

---

### 7. Kiểm tra lịch sử giao dịch

<button onclick="copyToClipboard('code13')">Copy</button>

<pre id="code13">
solana transaction-history <PUBLIC_KEY>
</pre>

📌 **Giải thích**: Xem lịch sử giao dịch của một địa chỉ ví.

---

### 8. Triển khai Smart Contract (Program)

<button onclick="copyToClipboard('code14')">Copy</button>

<pre id="code14">
solana program deploy <ĐƯỜNG_DẪN_TỚI_TỆP_BPF>
</pre>

📌 **Giải thích**: Triển khai một chương trình đã biên dịch (BPF) lên blockchain.

Ví dụ:
<button onclick="copyToClipboard('code15')">Copy</button>

<pre id="code15">
solana program deploy ./dist/program/my_program.so
</pre>

---

### 9. Kiểm tra danh sách các tài khoản thuộc ví

<button onclick="copyToClipboard('code16')">Copy</button>

<pre id="code16">
solana account <PUBLIC_KEY>
</pre>

📌 **Giải thích**: Hiển thị thông tin chi tiết về tài khoản Solana, bao gồm số dư, owner, v.v.

---

### 10. Chạy Validator Node (chỉ dành cho node operator)

<button onclick="copyToClipboard('code17')">Copy</button>

<pre id="code17">
solana-validator --identity ~/validator-keypair.json --rpc-port 8899 --entrypoint entrypoint.mainnet-beta.solana.com:8001
</pre>

📌 **Giải thích**: Chạy một validator node để tham gia mạng lưới Solana.

---

### 11. Kiểm tra thông tin về một Block

<button onclick="copyToClipboard('code18')">Copy</button>

<pre id="code18">
solana block <BLOCK_SLOT>
</pre>

📌 **Giải thích**: Xem thông tin về một block trên Solana.

---

### 12. Kiểm tra trạng thái của một giao dịch

<button onclick="copyToClipboard('code19')">Copy</button>

<pre id="code19">
solana confirm <TRANSACTION_SIGNATURE>
</pre>

📌 **Giải thích**: Kiểm tra trạng thái giao dịch bằng Transaction Signature.

Ví dụ:
<button onclick="copyToClipboard('code20')">Copy</button>

<pre id="code20">
solana confirm 5H8vQ...as6
</pre>
