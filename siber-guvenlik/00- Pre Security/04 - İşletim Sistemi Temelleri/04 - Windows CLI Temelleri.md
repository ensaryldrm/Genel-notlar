## 1. Dosya Sistemi ve Gezinme Komutları

Windows dosya sisteminde klasörler arasında geçiş yapmak ve içerikleri görüntülemek için kullanılan temel komutlar:

* **`cd` (Change Directory):** Tek başına yazıldığında şu an bulunduğunuz dizinin tam yolunu (örn: `C:\Users\Administrator`) gösterir.
  * **`cd <klasor_adi>`:** Belirtilen klasörün içine girmeyi sağlar. (Örn: `cd Documents`)
  * **`cd ..` :** Bir üst klasöre (seviyeye) dönmenizi sağlar.
* **`dir` (Directory):** Bulunduğunuz klasördeki görünür dosya ve alt klasörleri listeler.
  * **`dir /a`:** Windows tarafından varsayılan olarak gizlenmiş (hidden) dosyalar da dahil olmak üzere her şeyi listeler.

---

## 2. Dosya Arama ve Okuma

Kayıp dosyaları bulmak veya içeriklerini doğrudan komut satırından okumak için kullanılır:

* **`dir /s <dosya_adi>`:** Bulunduğunuz dizinden başlayarak tüm alt klasörlerde belirtilen dosyayı arar ve bulursa tam dosya yolunu gösterir. (Örn: `dir /s task_brief.txt`)
* **`type <dosya_adi>`:** Bir metin dosyasının içeriğini doğrudan terminal ekranına yazdırmak (okumak) için kullanılır. (Örn: `type task_brief.txt`)

---

## 3. Sistem ve Ağ Bilgisi Toplama

Siber güvenlik uzmanlarının bir sisteme girdiklerinde ortamı tanımak ve "sağlık kontrolü" yapmak için kullandıkları keşif komutları:

* **`whoami`:** O an sisteme hangi kullanıcı hesabıyla giriş yaptığınızı (izin düzeyinizi anlamak için) gösterir.
* **`hostname`:** Üzerinde çalıştığınız bilgisayarın ağdaki adını yazdırır.
* **`systeminfo`:** İşletim sisteminin sürümü (OS Version), mimarisi (32-bit / 64-bit) ve sistem türü gibi donanım/yazılım detaylarını listeler.
* **`ipconfig`:** Makinenin ağ yapılandırmasını gösterir. Özellikle şu iki bilgi için kritik öneme sahiptir:
  * **IPv4 Address:** Bilgisayarın ağdaki IP adresi.
  * **Default Gateway:** Varsayılan Ağ Geçidi (genellikle yönlendiricinin/modemin IP adresi).

---

## Neden Önemli?
* GUI'de (grafik arayüzde) her şey görünür değildir, dosyalar gizlenmiş olabilir.
* Sorun giderirken veya analiz yaparken menüler arasında kaybolmak yerine hızlı yanıtlar alınır.
* Komut satırı araçları otomasyona (script yazımına) çok daha uygundur.