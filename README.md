# testnet
for testnet nulink
1- sudo apt update && sudo apt upgrade -y

2- apt install python3-pip -y

3- wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.10.23-d901d853.tar.gz

4- tar -xvzf geth-linux-amd64-1.10.23-d901d853.tar.gz

5- cd geth-linux-amd64-1.10.23-d901d853/

6-  ./geth account new --keystore ./keystore

-----------copy all code and save to notpad

-----------send 0.1 tbnb (bnb test) to address pubic 

7- cd $home

8- docker pull nulink/nulink:latest   please before run code install docker

9- cd /root

10- mkdir nulink

11- cp xxxxxxxxxxxxxxxxxxxxx /root/nulink  please insert address secret key file 

example : cp /root/geth-linux-amd64-1.10.23-d901d853/keystore/UTC--2022-09-16T16-46-42.233370072Z--e686bf9b57cec541e0f46f2c0a41bc8836b9b270 /root/nulink

12- chmod -R 777 /root/nulink

13- pip install virtualenv

14- virtualenv /root/nulink-venv

15- source /root/nulink-venv/bin/activate

16- wget https://download.nulink.org/release/core/nulink-0.2.0-py3-none-any.whl --no-check-certificate

17- 1 pip install nulink-0.2.0-py3-none-any.whl


17.2. pip install --upgrade pip


18- source /root/nulink-venv/bin/activate

19- python -c "import nulink"

20- nulink --help

21- export NULINK_KEYSTORE_PASSWORD=xxxxxxxxxxxx  please input password 
22- export NULINK_OPERATOR_ETH_PASSWORD=xxxxxxxxxx  please input password

23-
docker run -it --rm \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
nulink/nulink nulink ursula init \
--signer keystore:///code/xxxxxxxxxxxxxxxxxxxxxxx \
--eth-provider https://data-seed-prebsc-2-s2.binance.org:8545/ \
--network horus \
--payment-provider https://data-seed-prebsc-2-s2.binance.org:8545/ \
--payment-network bsc_testnet \
--operator-address yyyyyyyyyyyyyyy \
--max-gas-price 100

Replace xxxxxxxxxxx by the your keystore file of the Worker
Remplace yyyyyyy by your operator adress

for example :
docker run -it --rm \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
nulink/nulink nulink ursula init \
--signer keystore:///code/UTC--2022-09-16T16-46-42.233370072Z--e686bf9b57cec541e0f46f2c0a41bc8836b9b270 \
--eth-provider https://data-seed-prebsc-2-s2.binance.org:8545/ \
--network horus \
--payment-provider https://data-seed-prebsc-2-s2.binance.org:8545/ \
--payment-network bsc_testnet \
--operator-address 0xe686bf9B57CEC541e0F46F2c0a41BC8836B9B270 \
--max-gas-price 100


24- این کد نیست توضیحات است

 Take a screenshot of your seedphrase

Now press y and ENTER

again input seedphrase

Save all info on a notepad

25- docker run --restart on-failure -d \
--name ursula \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
-e NULINK_OPERATOR_ETH_PASSWORD \
nulink/nulink nulink ursula run --no-block-until-ready

26- docker logs -f ursula

Press CTRL+C to stop the logs
