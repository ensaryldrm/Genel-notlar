## 1. Paketler ve Çerçeveler (Packets vs. Frames)
Büyük veriler ağ üzerinde tek seferde gönderilmez; darboğazı önlemek için küçük veri parçacıklarına bölünürler. Ancak OSI modelinde bu veri parçaları bulundukları katmana göre farklı isimlendirilirler:

- **Paket (Packet):** OSI 3. Katmanından (Ağ Katmanı) gelir. İçerisinde IP başlıkları (gönderen/alan IP vb.) ve asıl veri yükünü barındırır.
- **Çerçeve (Frame):** OSI 2. Katmanından (Veri Bağı Katmanı) gelir. Paketi içine alarak **kapsüller (encapsulate)** ve üzerine MAC adresi gibi fiziksel iletim bilgilerini ekler.

> [!tip] Posta Analojisi
> Çerçeveyi bir **zarf**, paketi ise içindeki **mektup** olarak düşünebilirsiniz. Zarf, mektubu bir noktadan diğerine taşımak için kullanılır. Alıcı zarfı (çerçeveyi) açtığında, asıl mektubu (paketi) nasıl okuyacağını veya yönlendireceğini anlar.

### Önemli IP Paketi Başlıkları (Headers)
Bir IP paketi hedefe giderken beraberinde şu kritik bilgileri taşır:
- **Yaşam Süresi (TTL - Time to Live):** Paketin ağda sonsuza kadar dolaşıp trafiği tıkamasını önleyen zaman aşımı/adım sayacıdır.
- **Sağlama Toplamı (Checksum):** Verinin yolda bozulup bozulmadığını kontrol eden hata denetim değeridir.
- **Kaynak (Source) ve Hedef (Destination) Adresi:** Gönderenin ve alıcının IP adresleridir.

---

## 2. İletişim Protokolleri: TCP ve UDP
Verilerin cihazlar arasında nasıl taşınacağını belirleyen iki ana kural setidir.

### A. TCP (İletim Kontrol Protokolü)
OSI modelinin özetlenmiş hali olan 4 katmanlı TCP/IP modelinin temel protokolüdür. 
- **Bağlantı Tabanlıdır (Connection-based):** Veri aktarılmadan önce istemci ve sunucu arasında zorunlu bir bağlantı kurulur.
- **Güvenilirdir:** Verilerin eksiksiz ve doğru sırayla iletilmesini garanti eder (Checksum ve Sıra Numaraları ile).
- **Yavaştır:** Sürekli kontrol ve onay mekanizması olduğu için daha fazla işlem gücü gerektirir ve yavaştır. (Örn: Web gezintisi, dosya indirme).

#### TCP Başlıkları
TCP paketleri IP başlıklarına ek olarak kendi başlıklarını da içerir:
- **Kaynak/Hedef Portu:** İletişimin yapıldığı kapı numaralarıdır.
- **Sıra Numarası (Sequence) ve Onay Numarası (ACK):** Paketlerin sıraya dizilmesini ve ulaşıp ulaşmadığının onaylanmasını sağlar.

#### Üçlü El Sıkışma (Three-Way Handshake)
TCP'de güvenilir bir bağlantı kurmak için iletişim başlamadan önce gerçekleşen 3 adımlı zorunlu süreçtir:
1. **SYN (İstemci):** "Seninle senkronize olmak (bağlantı kurmak) istiyorum. Benim başlangıç numaram bu."
2. **SYN/ACK (Sunucu):** "Talebini onaylıyorum (ACK). Ben de seninle senkronize olmak istiyorum, benim başlangıç numaram da bu (SYN)."
3. **ACK (İstemci):** "Senin onayını aldım, bağlantı kuruldu. Veri göndermeye başlıyorum."

> [!info] Bağlantıyı Kapatma (FIN)
> İletişim bittiğinde sistemi meşgul etmemek için cihazlardan biri **FIN (Finish)** paketi gönderir. Karşı taraf da bunu onaylar ve bağlantı temiz bir şekilde kapatılır. Acil ve sorunlu kapanışlarda ise **RST (Reset)** paketi kullanılır.

### B. UDP (Kullanıcı Veri Bloğu Protokolü)
TCP'nin aksine **durumsuz (stateless)** ve garantisiz bir protokoldür.
- **Hızlıdır:** El sıkışma, bağlantı kurma veya paket onaylama gibi süreçleri yoktur. Veriyi direkt yollar.
- **Güvenilmezdir:** Verinin ulaşıp ulaşmadığını veya doğru sırayla gidip gitmediğini umursamaz.
- **Kullanım Alanı:** Veri kaybının tolere edilebildiği ancak hızın kritik olduğu durumlar (Örn: Canlı yayınlar, sesli sohbetler, oyunlar).

---

## 3. Portlar (Bağlantı Noktaları)
Portlar, gelen verilerin cihaz içinde hangi uygulamaya veya hizmete gideceğini belirleyen sanal kapılardır (Bir limana yanaşan farklı tipteki gemiler gibi düşünülebilir). 
- Bilişimde `0` ile `65535` arasında numaralandırılırlar.
- `0 - 1024` arasındaki portlar evrensel **Yaygın Portlar (Common Ports)** olarak standartlaştırılmıştır.

### Sık Kullanılan Yaygın Portlar
| Protokol | Port | Açıklama |
| :--- | :--- | :--- |
| **FTP** | `21` | Dosya Aktarım Protokolü (Sunucudan dosya indirme/yükleme). |
| **SSH** | `22` | Güvenli Kabuk (Sistemlere uzaktan güvenli ve komut satırı üzerinden bağlantı). |
| **HTTP** | `80` | Şifresiz web trafiği (Web sitelerini görüntüleme). |
| **HTTPS** | `443` | Şifreli, güvenli web trafiği. |
| **SMB** | `445` | Sunucu Mesaj Bloğu (Ağ üzerinden dosya ve yazıcı paylaşımı). |
| **RDP** | `3389` | Uzak Masaüstü Protokolü (Görsel arayüz ile başka bir bilgisayara bağlanma). |

*Not: Standart dışı bir port kullanılmak istenirse (Örn: 80 yerine 8080), IP adresinin sonuna iki nokta ile eklenmelidir. (Örn: `192.168.1.100:8080`)*