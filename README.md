# nilion-node
1. Chuẩn bị
  testnet nillion thì cần chuẩn bị 1 ví Keplr, 
   
  truy cập https://chains.keplr.app tìm Nillion và add network vào ví Keplr.
  
  vào ví Keplr, chọn “setting” -> “General” -> “Manage chain Visibility” -> chọn mạng Nillion và save lại ở ví Keplr là hoàn thành.
  
  truy cập https://faucet.testnet.nillion.com, 
  
  dán ví Nillion vừa thêm vào Keplr ở bước trên để nhận token $NIL testnet.
  
  Vào testnet.ping.pub/nillion 
  thực hiện  “Delegate” ở mục Staking và “Voting” ở mục Governance.

2. chạy node:
1. Update: 

sudo apt-get update && sudo apt-get upgrade -y

2. Cài đặt docker:

  sudo apt install apt-transport-https ca-certificates curl software-properties-common
  
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
  
  echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
  sudo apt-get update
  
  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y
  
  docker --version

3. Cài đặt node Nillion:

  docker pull nillion/verifier:v1.0.1
  
  mkdir -p nillion/verifier
  
  docker run -v ./nillion/verifier:/var/tmp nillion/verifier:v1.0.1 initialise

4. Coppy account id & Public Key paste vào trang verify của Nillion

5.  Vào trang Faucet, Faucet NIL testnet vào địa chỉ ví (là cái account id vừa mới lấy trong terminal)

6. Cuối cùng chạy lệnh này:

docker run -v ./nillion/verifier:/var/tmp nillion/verifier:v1.0.1 verify --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com"

kèo này cần 0.05 ETH trên mạng chính để xác minh ae cân nhắc 
