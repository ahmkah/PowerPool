<h1 align="center"> Power Argent Standalone Installation </h1>




# My VPS:
2CPU - 4 RAM - 80 SSD
Ubuntu 22.04 



# STEP-1, Let's update our server:
```console
sudo apt-get update && sudo apt-get upgrade -y
```


# STEP-2, Docker and Docker Compose installing (enter the commands one by one):
```console

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
sudo systemctl enable docker

docker --version

sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version

```


# STEP-3, Let's download the necessary packages:
```console
sudo apt install git
sudo apt install nodejs
sudo apt install npm
```


# STEP-4, Let's clone sepolia-agent-standalone:
```console
git clone https://github.com/eitelvolkerts/sepolia-agent-standalone
```


# STEP-5,Let's clone the Power Agent:
```console
git clone https://github.com/powerpool-finance/powerpool-agent-v2-compose
cd powerpool-agent-v2-compose
npm i
```


# STEP-6, UTC--2023-08-18T09-32-40.364Z--8ccf, from which we received the PowerArgent backup..... our file with a Winscp-style application
## let's move it to "sepolia-agent-standalone/keys/" and delete the file that says "yourkeygoeshere"..
## Don't forget to correct the necessary places in the following file and change the Worker Address and Password, save and exit ( CTRL+X y enter)

## IMPORTANT NOTE: The RPC you use will not be public as it has been prohibited by the Power Pool team. You have two options: either set up a separate VPS with a Sepolia ETH Full Node and obtain an RPC from there, or purchase a private RPC at a cost. Those using public RPCs will not be eligible for rewards.
```console
nano sepolia-agent-standalone/config/main.yaml

> rpc: 'wss://sepolia-geth-XXXXXXXX'
> agents:
>           '0xbdE2Aed54521000DC033B67FB522034e0F93A7e5':
```
![image](https://github.com/ahmkah/PowerPool/assets/99053148/af846c7d-001a-4752-90c2-892795e1fa26)


# STEP-7, Now We will Run the Node:
```console

cd sepolia-agent-standalone

docker-compose pull

docker compose up -d
```

# To delete the docker container, enter the following command:
```console

docker compose down --rmi local
```


# STEP-8, Let's do a Log check:
```console

docker logs -f sepolia-agent-standalone-bot-1
```

# STEP-9, Enter the command below to save the Log file:
```console
docker logs sepolia-agent-standalone-bot-1 >& powerargentlogfile.log

```

<h1 align="center"> Power Argent Standalone Update </h1>

# STEP-1, first we update the powerargent repo

```console
cd sepolia-agent-standalone
git pull
npm i
```

# STEP-2, delete the docker container, enter the following command:
```console

docker compose down --rmi local
```

# STEP-3, Now We will Run the Node:
```console

docker-compose pull

docker compose up -d
```




