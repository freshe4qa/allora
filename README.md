<p align="center">
  <img height="100" height="auto" src="https://github.com/user-attachments/assets/762e2a94-92e0-4063-874b-dea77488f474">
</p>

# Allora Testnet — allora-testnet-1

Official documentation:
>- [Validator setup instructions](https://docs.allora.network/)

Explorer:
>- [https://explorer.testnet-1.testnet.allora.network/allora%20testnet](https://explorer.testnet-1.testnet.allora.network/allora%20testnet)

### Minimum Hardware Requirements
 - 2x CPUs; the faster clock speed the better
 - 4GB RAM
 - 5GB of storage (SSD or NVME)

### Recommended Hardware Requirements 
 - 4x CPUs; the faster clock speed the better
 - 8GB RAM
 - 100GB of storage (SSD or NVME)

 - Ubuntu 22.04

Для привязки кошелька Вам потребуется кошелек Keplr. Вам нужно будет создать в нем новый кошелек.

После чего переходим на [сайт](https://app.allora.network?ref=eyJyZWZlcnJlcl9pZCI6ImI0MzkyYmFlLTAwMDQtNDFjNS1iZWViLWVjMmYzYjM3ZDEyYSJ9) и подключаем кошелек.

![image](https://github.com/user-attachments/assets/ef272e71-f3e2-41d9-b9be-f5606ab68cd3)

Устанавливаем ноду:

``sudo apt update & sudo apt upgrade -y``

``sudo apt install ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev curl git wget make jq -y``

Добавляем сеть Allora-Testnet через [сайт](https://explorer.testnet.allora.network/wallet/keplr?chain=testnet).

![image](https://github.com/user-attachments/assets/4c60a01c-2089-4362-94e0-b3c57f3b481a)

Копируем $uallo адрес

![image](https://github.com/user-attachments/assets/54002a57-99ae-43be-a785-58da68ba41bd)

![image](https://github.com/user-attachments/assets/1a814b40-71a9-4879-ba28-5780de03e08a)

![image](https://github.com/user-attachments/assets/2d003f90-643d-4898-b506-d3c47d3ae31c)

Отправляемся к [крану](https://faucet.testnet-1.testnet.allora.network/) и запрашиваем тестовые токены $uAllo

![image](https://github.com/user-attachments/assets/228eb133-a922-4b7c-87f2-1c6348af0829)

Продолжаем установку ноды:

``sudo apt install apt-transport-https ca-certificates curl software-properties-common -y``

``curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -``

``sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"``

``sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y``

``sudo apt install apt-transport-https ca-certificates curl software-properties-common -y``

``apt install docker-compose -y``

``sudo rm -rf /usr/local/go``

``curl -L https://go.dev/dl/go1.21.6.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local``

``echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile``

``source .bash_profile``

``git clone https://github.com/allora-network/basic-coin-prediction-node``

``cd basic-coin-prediction-node``

``cp .env.example .env``

``nano .env``

Заполняем данные:

TOKEN=ETH
TRAINING_DAYS=30
TIMEFRAME=4h
MODEL=SVR
REGION=US
DATA_PROVIDER=binance
CG_API_KEY=

Сохраняем CTRL + O, CTRL + X

``cp config.example.json config.json``

``nano config.json``

Заполняем данные:

![Termius_GosdgAOSui](https://github.com/user-attachments/assets/d9cb6362-cdf8-4508-9cea-afa11251382f)

Пример:

{
  "wallet": {
    "addressKeyName": "test",
    "addressRestoreMnemonic": "staff worry museum egg goddess expect dolphin merit come space combine alpha zero holiday solution >    "alloraHomeDir": "",
    "gas": "1000000",
    "gasAdjustment": 1.0,
    "nodeRpc": "https://sentries-rpc.testnet-1.testnet.allora.network/",
    "maxRetries": 1,
    "delay": 1,
    "submitTx": true
  },
"worker": [
      {
        "topicId": 1,
        "inferenceEntrypointName": "api-worker-reputer",
        "loopSeconds": 5,
        "parameters": {
          "InferenceEndpoint": "http://localhost:8000/inference/{Token}",
          "Token": "ETH"
        }
      },
      // worker providing inferences for topic ID 2
      {
        "topicId": 2, 
        "inferenceEntrypointName": "api-worker-reputer",
        "loopSeconds": 5,
        "parameters": {
          "InferenceEndpoint": "http://localhost:8000/inference/{Token}", // the specific endpoint providing inferences
          "Token": "ETH" // The token specified in the endpoint
        }
      }
    ] 
  }

В этом поле вписываем свою фразу кошелька "addressRestoreMnemonic"



``git clone https://github.com/allora-network/allora-offchain-node``

``cd allora-offchain-node``

``cp config.example.json config.json``

``nano config.json``

В этом поле вписываем свою фразу кошелька "addressRestoreMnemonic"

Сохраняем CTRL + O, CTRL + X

``chmod +x init.config ./init.config``

``docker compose build``

``docker compose build``


Полезные команды:

Вывод ноды:

``curl http://localhost:8000/inference/ETH``

Удалить ноду:

``rm -rf allora.sh allora-chain/ basic-coin-prediction-node/``
