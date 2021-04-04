# multi-perspective-pm-chain

### Installation
* Make sure that `Docker` and `Docker Compose` have been installed in your computer. The following image show that how to check them;
![alt text](https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/docker-check.png)


* 
1. Docker ve Docker Compose'un bilgisayarınızda yüklü olduğuna emin olun.
2. Ek'te yer alan yaml dosyasını herhangi bir dizine indirin.
3. İndirmeyi yaptığınız dizinden terminal açın ve "docker-compose up" komutunu çalıştırın.
4. Burada Dockerhub a yüklediğim image dosyalarını çekecek burası uzun sürebilir (yaklaşık 12-13 GB).
5. İşlemin sonunda yukarıdaki gibi 3 adet container oluşması gerekiyor (yukarıdaki ekran Docker Desktop dan alındı, yüklediğiniz image ve container larınızı daha kolay görmeyi sağlıyor).
![alt text](https://github.com/burakcanekici/multi-perspective-pm-chain/blob/main/image/01.PNG)
6. Ardından listede "mp-fabricchain" contanier ının üzerine gelirseniz hemen yanında 5 adet buton çıkacak buradan ikinci sıradaki CLI olana tıklayın.
7. Burada sırasıyla "sudo su", "cd pm-network", ve /bin/bash _scripts/network-up.sh" ile blockchain network ümüzü ayağa kaldırıyoruz.
8. Yukarıdaki gibi done mesajını aldıysak blockchain network ayakta demektir.
9. Buradan sonra POST,GET, ve PUT request leri atacağız, bunun için ben Postman kullanıyorum.
10. İlk başta Control-flow perspektifi için POST methodunu kullanacağız, bunun için kullanacağımız URI "http://localhost:0146/api/datamodel" ve body sine koyacğımız parametreler aşağıdaki gibidir. Burada "file" parametresi Control-flow perspektifinin çıktısı olan pnml dosyasıdır, "model" parametresi de birden fazla model tutulabiliyor ilgili modelin id'si gibi değerlendirilebilir bunu istediğiniz sayıyı verebilirsiniz. Yani aynı event log için aynı model numarası üzerinden ilerleyin.
11. Ardından Data ve Resource perspektifleri için PUT methodunu kullanacağız, bunun için de aynı URI bilgisini kullanacağız. Burada Data perspektifi için pnml dosyası ve Resource perspektifi için OrgModel dosyaları "file" parametresine eklenecek, "model" parametresine güncellenmek istenen model numarası girilecek, ve "perspective" parametresine uygulanan perspektife göre "D" veya "R" girilecek.
12. Bu requestlerin sonucunda beklediğimiz mesaj aşağıdaki gibi olmalıdır.
H* erhangi bir adımda çıktı almak istersekte GET methodunu kullanacağız, fakat bu sefer diğer yöntemlerden farklı olarak parametremizi body içinde yollamayacağız. Aşağıdaki gibi "model" parametresini istediğiniz modelin numarasını vereceğiz. Burada sonuç olarak bpmn dosyası ineceği için sağ tarafta yer alan "Send" butonu yerine yanındaki okta ile beliren "Send and Download" butonunu kullanacağız çünkü dosya indirme işlemi var ise "Send" yerine bu kullanılmalı.
