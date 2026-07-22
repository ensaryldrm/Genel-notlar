# İleri Ağ Kavramları ve Protokoller

## 1. Yerel Ağ (LAN) Topolojileri
Topoloji, bir ağın fiziksel veya mantıksal tasarımını ifade eder.

### Yıldız (Star) Topolojisi
Cihazların anahtar (switch) veya dağıtıcı (hub) gibi merkezi bir cihaza bağlanmasıyla oluşur. Günümüzde en yaygın kullanılan topolojidir.
- **Avantajları:** Ölçeklenebilirdir; ağa yeni cihaz eklemek kolaydır.
- **Dezavantajları:** Fazla kablolama ve donanım gerektirdiğinden maliyetlidir. Merkezi cihaz (switch/hub) bozulursa ona bağlı tüm ağ çöker.

### Ortak Yollu (Bus) Topoloji
Tüm cihazların "omurga kablosu" (backbone) adı verilen tek bir ana hatta bağlandığı topolojidir.
- **Avantajları:** Düşük donanım ve kablolama maliyeti ile kurulumu kolaydır.
- **Dezavantajları:** Tüm veri aynı kablodan geçtiği için aynı anda veri akışında darboğaza (bottleneck) çok yatkındır. Omurga kablosu koparsa tüm ağ tamamen çöker.

### Halka (Ring) Topolojisi
Cihazların bir döngü oluşturacak şekilde doğrudan birbirine bağlandığı ağdır. Veri tek yönde ilerler.
- **Avantajları:** Aynı anda çok veri taşınmadığı için darboğaza girme ihtimali düşüktür.
- **Dezavantajları:** Veri hedefe ulaşana kadar aradaki birçok cihazdan geçmek zorunda kalabilir. Ağdaki tek bir cihazın bozulması tüm ağı çökertebilir.

---

## 2. Ağ Donanımları: Switch ve Router

### Switch (Anahtar)
- **Amacı:** Yerel bir ağ (LAN) kurmak. Aynı ağ içindeki cihazları (bilgisayar, yazıcı vb.) birbirine bağlar.
- **Çalışma Mantığı:** Hangi cihazın hangi porta bağlı olduğunu (MAC adresleriyle) hafızasında tutar. Gelen veriyi ağdaki herkese dağıtmak yerine sadece hedef cihaza göndererek ağ trafiğini büyük ölçüde azaltır.

### Router (Yönlendirici)
- **Amacı:** Küçük ağları birleştirip büyük ağlar oluşturmak (Örn: Evinizdeki yerel ağı İnternet'e bağlamak).
- **Çalışma Mantığı:** İletişimi IP adresleri üzerinden kurar. Verilerin ağlar arasında hedefe giderken hangi rotayı izleyeceğine ("yönlendirme" - routing) karar verir.

---

## 3. Alt Ağlara Bölme (Subnetting)
Subnetting, büyük bir ağı kendi içinde daha küçük, yönetilebilir "alt ağlara" ayırma işlemidir.

- **Alt Ağ Maskesi (Subnet Mask):** Ağa sığabilecek maksimum cihaz sayısını belirler (Örn: `255.255.255.0`).
- Bir alt ağda IP adresleri üç farklı amaçla kullanılır:
  1. **Ağ Adresi:** Ağın başlangıcını belirtir ve cihazlara atanamaz (Örn: `192.168.1.0`).
  2. **Cihaz (Host) Adresi:** Alt ağdaki bir cihaza atanan kullanıma açık özel adrestir (Örn: `192.168.1.100`).
  3. **Varsayılan Ağ Geçidi (Default Gateway):** Ağ dışına (İnternet'e veya başka bir ağa) veri gönderebilen cihazın (genellikle Router) adresidir. Genelde ağın ilk veya son adresi olur (`192.168.1.1` veya `192.168.1.254`).

> [!NOTE] Subnetting'in Güvenlik Avantajı
> İşletmelerde departmanları veya farklı kullanıcı gruplarını birbirinden yalıtarak (Örn: Personel ağı ve Müşteri Wi-Fi ağını ayırmak) verilerin güvenliğini sağlar.

---

## 4. Adres Çözümleme Protokolü (ARP)
Cihazların bir ağ üzerinde birbirlerini donanımsal olarak bulmalarını sağlayan teknolojidir. 
- **Görevi:** Bir cihazın IP adresi ile o cihazın fiziksel MAC adresini eşleştirmek.

**İşleyiş Adımları:**
1. **ARP İsteği (Request):** Hedefin IP adresini bilen cihaz tüm ağa sorar: *"Bu IP adresi kimin? Bana MAC adresini söyle."*
2. **ARP Yanıtı (Reply):** Sadece o IP'ye sahip olan cihaz kendi MAC adresiyle özel olarak cevap verir.
- Cihazlar bu eşleşmeleri her defasında tekrar sormamak için **ARP Önbelleğine (Cache)** kaydederler.

---

## 5. Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP)
Ağa yeni bağlanan cihazlara otomatik olarak IP adresi ve ağ bilgileri atayan sistemdir. Ağı manuel yapılandırma zahmetinden kurtarır.

**İşleyiş Süreci:**
1. **Discover (Keşif):** IP'si olmayan cihaz ağda bir DHCP sunucusu arar.
2. **Offer (Teklif):** DHCP sunucusu cihaza uygun boş bir IP adresi teklif eder.
3. **Request (İstek):** Cihaz teklif edilen IP'yi kullanmak istediğini onaylar.
4. **ACK (Onay):** DHCP sunucusu işlemi onaylar ve cihaz IP adresini resmen kullanmaya başlar.