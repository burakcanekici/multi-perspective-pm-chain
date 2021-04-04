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
* If the network is brought up as the image above, we can interact with the fabric network via the API server developed and hosted by `mp-apiserver` container.
> In here, `POST`, `GET`, and `PUT` methods are used for interaction.
* I preferred `Postman` to send HTTP requests, but you can use whatever you want;


10. İlk başta Control-flow perspektifi için POST methodunu kullanacağız, bunun için kullanacağımız URI "http://localhost:0146/api/datamodel" ve body sine koyacğımız parametreler aşağıdaki gibidir. Burada "file" parametresi Control-flow perspektifinin çıktısı olan pnml dosyasıdır, "model" parametresi de birden fazla model tutulabiliyor ilgili modelin id'si gibi değerlendirilebilir bunu istediğiniz sayıyı verebilirsiniz. Yani aynı event log için aynı model numarası üzerinden ilerleyin.
11. Ardından Data ve Resource perspektifleri için PUT methodunu kullanacağız, bunun için de aynı URI bilgisini kullanacağız. Burada Data perspektifi için pnml dosyası ve Resource perspektifi için OrgModel dosyaları "file" parametresine eklenecek, "model" parametresine güncellenmek istenen model numarası girilecek, ve "perspective" parametresine uygulanan perspektife göre "D" veya "R" girilecek.
12. Bu requestlerin sonucunda beklediğimiz mesaj aşağıdaki gibi olmalıdır.
H* erhangi bir adımda çıktı almak istersekte GET methodunu kullanacağız, fakat bu sefer diğer yöntemlerden farklı olarak parametremizi body içinde yollamayacağız. Aşağıdaki gibi "model" parametresini istediğiniz modelin numarasını vereceğiz. Burada sonuç olarak bpmn dosyası ineceği için sağ tarafta yer alan "Send" butonu yerine yanındaki okta ile beliren "Send and Download" butonunu kullanacağız çünkü dosya indirme işlemi var ise "Send" yerine bu kullanılmalı.
