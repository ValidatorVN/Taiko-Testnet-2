# Taiko-Testnet-2

Chạy node dự án Taiko

    Cấu hình khuyến nghị:
    8-16 core
    32gb Ramm
    400Gb SSD
  
Thông tin tìm đọc:

    https://taiko.xyz/docs/guides/run-a-node
    
Cộng đồng chạy node VietNam:

    https://t.me/NodeValidatorVietNam
    
1/ Cập nhật hệ thống:

    sudo apt update && apt upgrade -y
    
2/ Cài đặt Docker:

    sudo apt-get update
    sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
    
    sudo mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
    sudo apt-get update -y
    
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    
3/ Tải clone Github dự án:

    git clone https://github.com/taikoxyz/simple-taiko-node.git
    cd simple-taiko-node
    
 4/ Taọ file .env và sửa đổi:
 
    cp .env.sample .env
    
 Sửa file:
 
    nano .env
    
 Kéo xuống phía dưới, để ý 2 dòng sau:
 
    L1_ENDPOINT_HTTP=
    L1_ENDPOINT_WS=
    
Lấy 2 thông tin này bằng cách đăng kí tài khoản FREE tại: https://dashboard.alchemy.com/
 
    Nhấn theo các bước sau: CREATE APP -> Đặt tên -> Chain: ETH -> Network: Sepholia -> Create App
    
Nhấn vào View Key sẽ thấy 2 dòng:

    https://eth-sepolia.g.alchemy.com/v2/pDv3yo41GYQhYJeBLZ8tL94cE
    
    wss://eth-sepolia.g.alchemy.com/v2/pDv3yo41GYQhYJeB
    
Để chạy Prover
Thay đổi dòng sau:
    
    ENABLE_PROVER=true
    L1_PROVER_PRIVATE_KEY=
    
(chỗ này dán PRIVATE KEY của bạn vào, vào Metamask Export, nhớ là dùng ví PHỤ để làm nhé)
    
    
Copy và dán vào VPS của bạn, sau đó nhấn lệnh theo thứ tự:

    Control O
    Enter
    Control X
    
5/ Chạy Node bằng lệnh:

    docker compose up -d
    
 Xoá node:
 
    docker compose down
    docker compose down -v
    rm -f .env
    
 Update node:
 
    control C
    
    docker compose pull
    docker compose restart
    
 Check logs:
 
    docker compose logs -f
    
6/ Faucet token testnet vào ví chạy node:

    https://sepolia-faucet.pk910.de/
    https://faucet-sepolia.rockx.com/
    
