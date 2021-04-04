# multi-perspective-pm-chain

## Installation
* Make sure that `Docker` and `Docker Compose` have been installed in your computer. The following image show that how to check them;

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/docker-check.png"></kbd>
</p>

* Download the `docker-compose.yaml` to any folder you want.
* Open cmd from where you download the `docker-compose.yaml` file into and execute the following command;
```
docker-compose up
```
* At the first time, the installation process could be long. If you see the containers in the Docker Desktop as the following image, the tool has been installed correctly;

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/containers.png"></kbd>
</p>

## The Tool

### Bring up the fabric network
* Open CLI for `mp-fabricchain` container and execute the following commands to bring the blockchain network up;
```
sudu su
cd pm-network
/bin/bash _scripts/network-up.sh
```

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/network-up.png"></kbd>
</p>

### Interact with the fabric network
* If the network is brought up as the image above, we can interact with the fabric network via the API server developed and hosted by `mp-apiserver` container. The API server is working on `http://localhost:0146/api/datamodel` path and `POST`, `GET`, and `PUT` methods are used for interaction.

| Method | Description | Parameters |
| --- | --- | --- |
| `GET` | Used for downloading the Data Model in BPMN format | `model` -> model number |
| `POST` | Used for recording the result of Control-Flow analysis to the fabric network | `model` -> model number <br/> `file` -> file (in **.pnml** format) |
| `PUT` | Used for updating the Data Model kept in fabric network, with the result of Decision or Resource analysis | `model` -> model number <br/> `file` -> file (in **.pnml** or **.xml** format) <br/> `perspective` -> perspective identifier, either **D** or **R** |
> I preferred `Postman` to send HTTP requests, but you can use whatever you want;

* In `POST` request, the `model` and `file` parameters should be filled properly as the following image. The `model` parameter is identifier for what you send in `file` parameter which should be output file of Control-Flow analysis. **The model will be kept in blockchain with this identifier and it will be updated or downloaded via this identifier during the `PUT` and `GET` requests.** <br/> *If the relevant method is executed successfully, `Transaction has been submitted` message will be returned from server.*

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/post.PNG"></kbd>
</p>

* In `PUT` request, the `model`, `perspective` and `file` parameters should be filled properly as the following image. The `model` parameter is identifier for what you send in `file` parameter which should be output file of Decision or Resource analysis and the `perspective` represents that it is result of either Decision or Resource analysis. **The model kept in blockchain will be updated via this identifier according to the perspective we want.** <br/> *If the relevant method is executed successfully, `Transaction has been submitted` message will be returned from server.*

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/put.PNG"></kbd>
</p>

* In `GET` request, only the `model` parameters should be filled properly as the following image. The `model` parameter is identifier for what you want to download in BPMN format. **The model kept in blockchain will be downloaded via this identifier.**<br/> *If the relevant method is executed successfully, the BPMN file will be downloaded.*

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/get.png"></kbd>
</p>

* On the other hand, the `mp-frontend` container hosts a frontend application that makes interaction with the API server without using `Postman` or this sort of applications. **This is not essential, but for optional.**

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/frontend.png"></kbd>
</p>

### Bring down the fabric network
* Open CLI for `mp-fabricchain` container and execute the following commands to bring the blockchain network down;
```
sudu su
cd pm-network
/bin/bash _scripts/network-down.sh
```

<p align="center">
  <kbd><img src="https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/network-down.png"></kbd>
</p>
