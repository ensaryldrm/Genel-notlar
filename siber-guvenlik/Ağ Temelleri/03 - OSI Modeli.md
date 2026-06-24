# OSI Modeli ve Ağ Katmanları

## OSI Modeline Giriş
OSI (Açık Sistemler Bağlantı) Modeli, ağa bağlı tüm cihazların verileri nasıl göndereceğini, alacağını ve yorumlayacağını belirleyen temel bir çerçevedir.
- **En Büyük Avantajı:** Farklı işlevlere ve tasarımlara sahip cihazların (farklı marka ve işletim sistemlerinin) ortak bir standart üzerinden sorunsuz iletişim kurmasını sağlar.
- **Kapsülleme (Encapsulation):** Verinin 7. katmandan 1. katmana doğru seyahat ederken her katmanda belirli işlemlerden geçerek yeni bilgi parçacıkları (başlıklar vb.) eklenmesi işlemidir.

---

## Katman 1: Fiziksel Katman (Physical Layer)
Ağ altyapısının en alt katmanıdır ve tamamen donanımın fiziksel bileşenleriyle ilgilidir.
- İletişim, ikili sayı sisteminde (1'ler ve 0'lar) elektrik sinyalleri kullanılarak yapılır.
- **Örnekler:** Ethernet kabloları, fiber optik kablolar, donanımsal portlar.

---

## Katman 2: Veri Bağı Katmanı (Data Link Layer)
İletimin fiziksel adreslemesine odaklanan katmandır.
- Ağ katmanından gelen IP paketlerine alıcı uç noktanın fiziksel **MAC adresini** ekler.
- Her bilgisayardaki **Ağ Arayüz Kartı (NIC)** bu katmanda çalışır.
- MAC adresleri donanıma kalıcı işlenmiştir ancak yazılımsal olarak taklit edilebilir (spoofing).
- Veriyi iletime uygun bir formatta (frame/çerçeve) hazırlamak bu katmanın görevidir.

---

## Katman 3: Ağ Katmanı (Network Layer)
Verilerin yönlendirilmesi (routing) işlemlerinin gerçekleştiği yerdir.
- İletişim **IP adresleri** (Örn: `192.168.1.100`) üzerinden yürütülür.
- **Yönlendirme (Routing):** Veri paketlerinin hedefe ulaşması için en uygun rotayı seçer. Rota seçilirken şunlara bakılır:
  - En kısa yol (en az cihaz/sıçrama noktası).
  - En güvenilir yol (kayıp yaşanmayan hat).
  - En hızlı fiziksel bağlantı (bakır yerine fiber hat gibi).
- **Protokoller:** OSPF, RIP.
- **Cihazlar:** Yönlendiriciler (Routers), bu katmanda çalıştıkları için "Katman 3 cihazları" olarak bilinir.

---

## Katman 4: Taşıma Katmanı (Transport Layer)
Verilerin cihazlar arasında nasıl iletileceğini belirler. Bu katmanda iki ana protokol öne çıkar: TCP ve UDP.

| Özellik | TCP (İletim Kontrol Protokolü) | UDP (Kullanıcı Veri Bloğu Protokolü) |
| :--- | :--- | :--- |
| **Güvenilirlik** | Verilerin doğruluğunu ve eksiksiz ulaşmasını garanti eder. | Ulaşıp ulaşmadığını kontrol etmez, garanti sunmaz. |
| **Hız** | Hata denetimi yaptığı için yavaştır. | Doğrudan gönderdiği için çok hızlıdır. |
| **Bağlantı Türü** | İletişim boyunca kesintisiz bağlantı (oturum) rezerve eder. | Bağlantı rezerve etmez, serbest veri akışı sağlar. |
| **Hata Denetimi** | Var. Eksik paket varsa baştan ister ve sıraya dizer. | Yok. Kayıp paketleri (örn. piksellenme) umursamaz. |
| **Kullanım Alanları** | Webde gezinme, e-posta, dosya indirme/paylaşma. | Video akışı (streaming), DNS, ARP, DHCP keşifleri. |

---

## Katman 5: Oturum Katmanı (Session Layer)
İki bilgisayar arasındaki iletişimi başlatır, sürdürür ve sonlandırır.
- Bağlantı kurulduğunda benzersiz bir **Oturum (Session)** oluşturulur.
- İletişim koparsa veya uzun süre kullanılmazsa oturumu kapatır.
- **Kontrol Noktaları (Checkpoints):** Veri iletimi sırasında kopma olursa, tüm veriyi baştan göndermek yerine sadece kaybolan en son parçaları göndererek bant genişliğinden tasarruf sağlar.

---

## Katman 6: Sunum Katmanı (Presentation Layer)
Ağdaki standardizasyonun ve çeviri işlemlerinin gerçekleştiği katmandır.
- Uygulama katmanına gelen/giden veriler için **çevirmen (translator)** görevi görür.
- Farklı e-posta istemcileri veya yazılımlar kullanılsa bile içeriğin her iki tarafta da aynı standartta görüntülenmesini sağlar.
- **Güvenlik:** Web sitelerindeki HTTPS iletişimi gibi veri şifreleme (encryption) işlemleri bu katmanda yapılır.

---

## Katman 7: Uygulama Katmanı (Application Layer)
Son kullanıcıya en yakın olan, kullanıcının verilerle etkileşime girdiği katmandır.
- Kullanıcıya işlemleri yapabilmesi için bir **Grafik Kullanıcı Arayüzü (GUI)** sunar.
- **Örnek Uygulamalar:** Web tarayıcıları (Chrome vb.), e-posta istemcileri, FileZilla gibi dosya transfer programları.
- **Protokoller:** Alan adlarını (site isimlerini) IP adreslerine çeviren **DNS** (Domain Name System) bu katmanda çalışır.