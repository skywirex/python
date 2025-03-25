# RetroDash


```
RetroDash/
├── main.py                 # Điểm khởi chạy chính của bot
├── config/
│   ├── config.yaml        # Cấu hình (API keys, node URLs, v.v.)
│   └── settings.py        # Cài đặt mặc định
├── wallets/
│   ├── wallet_manager.py  # Quản lý ví chung (tạo, lưu trữ, truy xuất)
│   └── key_manager.py     # Quản lý khóa (mã hóa, giải mã)
├── tools/                 # Thư mục công cụ chung ở cấp gốc
│   ├── evm_wallet_gen.py  # Tạo ví cho EVM
│   ├── sol_wallet_gen.py  # Tạo ví cho Solana
│   ├── utils.py           # Hàm tiện ích chung (dùng cho tất cả blockchain)
│   └── __init__.py        # Khởi tạo module
├── evm/                   # Nhóm blockchain tương thích EVM
│   ├── core/
│   │   ├── blockchain.py  # Logic chung cho EVM (gửi tx, kiểm tra số dư)
│   │   ├── transaction.py # Xử lý giao dịch EVM
│   │   └── __init__.py    # Khởi tạo module
│   ├── adapters/
│   │   ├── ethereum.py    # Adapter cho Ethereum
│   │   ├── bsc.py         # Adapter cho Binance Smart Chain
│   │   ├── polygon.py     # Adapter cho Polygon
│   │   └── __init__.py    # Khởi tạo module
│   └── __init__.py        # Khởi tạo module
├── solana/
│   ├── core/
│   │   ├── blockchain.py  # Logic riêng cho Solana
│   │   ├── transaction.py # Xử lý giao dịch Solana
│   │   └── __init__.py    # Khởi tạo module
│   ├── adapter.py         # Adapter cho Solana
│   └── __init__.py        # Khởi tạo module
├── gui/                   # Thư mục cho GUI (tương lai)
│   ├── __init__.py        # Khởi tạo module
│   ├── main_window.py     # Cửa sổ chính
│   └── widgets.py         # Thành phần giao diện
├── tests/
│   ├── test_evm.py        # Kiểm thử EVM
│   ├── test_solana.py     # Kiểm thử Solana
│   └── test_wallets.py    # Kiểm thử ví
├── logs/
│   └── bot.log            # Nhật ký hoạt động
├── requirements.txt       # Danh sách thư viện
└── README.md              # Hướng dẫn
```