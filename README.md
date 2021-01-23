# multi-perspective-pm-chain
Docker ve Docker Compose'un bilgisayarınızda yüklü olduğuna emin olun.
Ek'te yer alan yaml dosyasını herhangi bir dizine indirin.
İndirmeyi yaptığınız dizinden terminal açın ve "docker-compose up" komutunu çalıştırın.
Burada Dockerhub a yüklediğim image dosyalarını çekecek burası uzun sürebilir (yaklaşık 12-13 GB).image.png
İşlemin sonunda yukarıdaki gibi 3 adet container oluşması gerekiyor (yukarıdaki ekran Docker Desktop dan alındı, yüklediğiniz image ve container larınızı daha kolay görmeyi sağlıyor).
Ardından listede "mp-fabricchain" contanier ının üzerine gelirseniz hemen yanında 5 adet buton çıkacak buradan ikinci sıradaki CLI olana tıklayın.
Burada sırasıyla "sudo su", "cd pm-network", ve /bin/bash _scripts/network-up.sh" ile blockchain network ümüzü ayağa kaldırıyoruz.image.png
Yukarıdaki gibi done mesajını aldıysak blockchain network ayakta demektir.
Buradan sonra POST,GET, ve PUT request leri atacağız, bunun için ben Postman kullanıyorum.
İlk başta Control-flow perspektifi için POST methodunu kullanacağız, bunun için kullanacağımız URI "http://localhost:0146/api/datamodel" ve body sine koyacğımız parametreler aşağıdaki gibidir. Burada "file" parametresi Control-flow perspektifinin çıktısı olan pnml dosyasıdır, "model" parametresi de birden fazla model tutulabiliyor ilgili modelin id'si gibi değerlendirilebilir bunu istediğiniz sayıyı verebilirsiniz. Yani aynı event log için aynı model numarası üzerinden ilerleyin.image.png
Ardından Data ve Resource perspektifleri için PUT methodunu kullanacağız, bunun için de aynı URI bilgisini kullanacağız. Burada Data perspektifi için pnml dosyası ve Resource perspektifi için OrgModel dosyaları "file" parametresine eklenecek, "model" parametresine güncellenmek istenen model numarası girilecek, ve "perspective" parametresine uygulanan perspektife göre "D" veya "R" girilecek.image.png
Bu requestlerin sonucunda beklediğimiz mesaj aşağıdaki gibi olmalıdır.image.png
Herhangi bir adımda çıktı almak istersekte GET methodunu kullanacağız, fakat bu sefer diğer yöntemlerden farklı olarak parametremizi body içinde yollamayacağız. Aşağıdaki gibi "model" parametresini istediğiniz modelin numarasını vereceğiz. Burada sonuç olarak bpmn dosyası ineceği için sağ tarafta yer alan "Send" butonu yerine yanındaki okta ile beliren "Send and Download" butonunu kullanacağız çünkü dosya indirme işlemi var ise "Send" yerine bu kullanılmalı.image.png
