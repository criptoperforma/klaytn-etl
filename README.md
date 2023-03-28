

Importando o pacote klaytn-etl:
python
Copy code
import klaytn_etl
Configurando o endpoint do nó Klaytn:
python
Copy code
from klaytn_etl import KlaytnETL

etl = KlaytnETL(endpoint_uri='https://api.cypress.klaytn.net:8651')
Obtendo o bloco mais recente:
python
Copy code
latest_block = etl.get_latest_block()
Obtendo informações de um bloco específico:
python
Copy code
block = etl.get_block_by_number(12345)
Obtendo todas as transações de um bloco específico:
python
Copy code
transactions = etl.get_block_transactions(12345)
Importando o pacote Augmented-Reality:
python
Copy code
import augmented_reality
Inicializando a câmera para exibir imagens em tempo real:
python
Copy code
from augmented_reality import Camera

camera = Camera()
camera.start_preview()
Adicionando um objeto 3D em uma imagem:
python
Copy code
from augmented_reality import Image, Object3D

image = Image('path/to/image.jpg')
object_3d = Object3D('path/to/object.obj')

image.add_object(object_3d, x=100, y=100, z=0)
image.show()
Importando o pacote DexSniping-BSC-ERC20-Telegram-Alerts:
python
Copy code
import dex_sniping

config = dex_sniping.load_config('config.yaml')
Criando uma nova instância do bot Telegram:
python
Copy code
from dex_sniping import TelegramBot

bot = TelegramBot(config['telegram']['token'])
Enviando uma mensagem de teste para o bot Telegram:
python
Copy code
bot.send_message(config['telegram']['chat_id'], 'Test message')
Obtendo o saldo de uma carteira BSC:
python
Copy code
from dex_sniping import BscClient

client = BscClient()
balance = client.get_balance('0x123456789abcdef')
Obtendo informações sobre um token ERC20:
python
Copy code
from dex_sniping import Erc20Client

client = Erc20Client()
token_info = client.get_token_info('0x123456789abcdef')
Obtendo a lista de pares de negociação em uma exchange BSC:
python
Copy code
from dex_sniping import PancakeSwapClient

client = PancakeSwapClient()
pairs = client.get_pairs()
Verificando se uma transação foi confirmada na rede BSC:
python
Copy code
from dex_sniping import BscClient

client = BscClient()
tx_hash = '0x123456789abcdef'
is_confirmed = client.is_tx_confirmed(tx_hash)
Obtendo informações sobre um par de negociação em uma exchange BSC:
python
Copy code
from dex_sniping import PancakeSwapClient

client = PancakeSwapClient()
pair_address = '0x123456789abcdef'
pair_info = client.get_pair_info(pair_address)
Comprando um token em uma exchange BSC:
python
Copy code
from dex_sniping import PancakeSwapClient

client = PancakeSwapClient()
pair_address = '0x123456789abcdef'
token_to_buy = '0x987654321fedcba'
buy_amount = 1.0

client.buy_token(pair_address, token_to_buy, buy_amount)
Vendendo um token









# Klaytn ETL

Klaytn ETL lets you convert Klaytn blockchain data into convenient formats like JSONs, CSVs and relational databases.
This is a fork of [Ethereum ETL](https://github.com/blockchain-etl/ethereum-etl).

[Full documentation available here](http://klaytn-etl.readthedocs.io/).

***Notice: Klaytn ETL is still on the beta version. However, CLIs are all functional.***

## Quickstart
Install Klaytn ETL:

```bash
pip3 install klaytn-etl-cli
```

Export blocks and transactions

```bash
> klaytnetl export_blocks_and_transactions --start-block 0 --end-block 5000 \
--blocks-output blocks.json --transactions-output transactions.json
```

Export ERC20 and ERC721 transfers

```bash
> klaytnetl export_token_transfers --start-block 0 --end-block 5000 \
--output token_transfers.json
```

Export traces

```bash
> klaytnetl export_traces --start-block 0 --end-block 5000 \
--output traces.json
```

Find other commands [here](klaytnetl/cli/__init__.py).

For the latest version, check out the repo and call 
```bash
> pip3 install -e . 
> python3 klaytnetl.py
```

### Running in Docker

1. Install Docker https://docs.docker.com/install/

2. Build a docker image
    ```bash
    > docker build -t klaytn-etl:latest .
    > docker image ls
    ```

3. Run a container out of the image
    ```bash
    > docker run -v $HOME/output:/klaytn-etl/output klaytn-etl:latest export_all -s 0 -e 5499999 -b 100000
    > docker run -v $HOME/output:/klaytn-etl/output klaytn-etl:latest export_all -s 2018-01-01 -e 2018-01-01
    ```
