Block có 
- Metadata
- Transaction

Cryptographic Hash
- ETH: Keccak256 ~ SHA3

Address
- Dùng để gửi và nhận tài sản
- EOA
Wallet
- Cung cấp các địa chỉ
- Ex: Metamask, TrustWallet
Transactions
- Bất kì 1 hành động nào làm thay đổi blockchain đều được gọi là transaction
- Vòng đời
	- Build 1 transaction gồm các trường dữ liệu
	- Dùng private key để sign
	- Send lên blockchain
	- Chờ verify (từ validator node hoặc minor node)

[[Smart Contract - SMC]]

Gas
- Phí giao dịch 
- Chống spam
- Người gửi transactions trả phí gas
- Trả cho người ghi được block có chứa transaction lên blockchain
## Consensus Mechanism
- Proof of work
	- Ai đào được 1 khối và ghi lên blockchain => BTC mới được sinh ra để thưởng cho người đào

## Crypto Currency
- [[Bitcoin]], [[Ethereum]]