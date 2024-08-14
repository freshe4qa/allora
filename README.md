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

``sudo apt install ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev curl git wget make -y``

Добавляем сеть Allora-Testnet через [сайт](https://explorer.testnet.allora.network/wallet/keplr?chain=testnet).

![image](https://github.com/user-attachments/assets/4c60a01c-2089-4362-94e0-b3c57f3b481a)

Копируем $uallo адрес

![image](https://github.com/user-attachments/assets/54002a57-99ae-43be-a785-58da68ba41bd)

![image](https://github.com/user-attachments/assets/1a814b40-71a9-4879-ba28-5780de03e08a)

![image](https://github.com/user-attachments/assets/2d003f90-643d-4898-b506-d3c47d3ae31c)

Отправляемся к [крану](https://faucet.testnet.allora.network) и запрашиваем тестовые токены $uAllo

![image](https://github.com/user-attachments/assets/228eb133-a922-4b7c-87f2-1c6348af0829)

Продолжаем установку ноды:

``rm -rf allora.sh allora-chain/ basic-coin-prediction-node/``

``wget https://raw.githubusercontent.com/dxzenith/allora-worker-node/main/allora.sh && chmod +x allora.sh && ./allora.sh``

![image](https://github.com/user-attachments/assets/277c6707-7074-4c56-8ad8-98c3e5a9207c)

Далее потребуется вписать сид фразу от кошелька

![image](https://github.com/user-attachments/assets/778d5c64-9e91-486d-8136-541778924e5e)

После нам выдадут HEAD-ID — копируем и вставляем

Еще раз сид фразу и в последнем поле вписываем 1

![image](https://github.com/user-attachments/assets/87f94d78-8c52-4193-9bd8-d7e0231aae57)

Далее нам потребуется именно этот контейнер для проверки логов:

![image](https://github.com/user-attachments/assets/756d823c-a2f0-4bb1-a07b-878a565df8e7)

``docker logs -f ВАШ_COINTERID``

После этого выполняем данный [квест](https://app.galxe.com/quest/AlloraNetwork/GCps2tzW3B)

Полезные команды:

Статус ноды:

``curl --location 'http://localhost:6000/api/v1/functions/execute' \
--header 'Content-Type: application/json' \
--data '{
    "function_id": "bafybeigpiwl3o73zvvl6dxdqu7zqcub5mhg65jiky2xqb4rdhfmikswzqm",
    "method": "allora-inference-function.wasm",
    "parameters": null,
    "topic": "1",
    "config": {
        "env_vars": [
            {
                "name": "BLS_REQUEST_PATH",
                "value": "/api"
            },
            {
                "name": "ALLORA_ARG_PARAMS",
                "value": "ETH"
            }
        ],
        "number_of_nodes": -1,
        "timeout": 2
    }
}'``

Проверка обновления:

``curl http://localhost:8000/update``

Вывод ноды:

``curl http://localhost:8000/inference/ETH``

Удалить ноду:

``rm -rf allora.sh allora-chain/ basic-coin-prediction-node/``









