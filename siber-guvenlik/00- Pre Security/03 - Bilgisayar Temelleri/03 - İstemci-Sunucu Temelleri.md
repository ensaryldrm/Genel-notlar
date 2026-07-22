## 1. İstemci-Sunucu (Client-Server) Modeli

Bilgisayar sistemlerinin etkileşimini bir restoranın paket servis hizmetine benzetebiliriz:
* **İstemci (Client):** Hizmeti veya veriyi talep eden taraftır (Siparişi veren müşteri veya web sitesini açmak isteyen tarayıcı). **Talebi her zaman istemci başlatır.**
* **Sunucu (Server):** İstemcinin talebini alıp işleyen ve istenen hizmeti/veriyi sunan sistemdir (Siparişi hazırlayan restoran veya web sayfasını barındıran donanım).
* **İstek ve Yanıt (Request & Response):** İstemcinin veriyi istemesi "İstek", sunucunun durumu değerlendirip (başarılı veya hatalı) sonucu döndürmesi "Yanıt" olarak adlandırılır.

---

## 2. İletişimin Temel Taşları

### Protokol (Protocol)
Sistemlerin birbiriyle nasıl iletişim kuracağını belirleyen kurallar bütünüdür (Ortak dil). Şunları tanımlar:
* İstemci ve sunucunun anladığı komutlar (Örn: `GET`).
* İsteğin nasıl yapılandırılacağı (Sözdizimi).
* Hangi tür isteğe veya hatalara nasıl bir yanıt verileceği.

### Bağlantı Noktası (Port)
Bir sistem üzerinde çalışan **belirli bir hizmeti** tanımlamak için kullanılır. Bir sunucu aynı anda birden fazla hizmet (web, e-posta, dosya transferi vb.) sunabilir. İstemcinin doğru hizmete ulaşabilmesi için doğru "kapıdan" yani porttan bağlanması gerekir.

### DNS ve IP Adresi
* **IP Adresi:** İnternetteki bir bilgisayarın veya sunucunun ağ üzerindeki tam koordinatıdır (Örn: `127.0.0.1`). Sistemlerin ev adresi gibidir.
* **DNS (Alan Adı Sistemi):** Karmaşık IP adreslerini akılda kalıcı alan adlarına (Örn: `tryhackme.com`) çeviren, internetin GPS cihazı veya telefon rehberidir.

---

## 3. HTTP(S) Protokolü ve İstekler

**HTTP (Hiper Metin Transfer Protokolü):** World Wide Web (web siteleri) için kullanılan, temel iletişim protokolüdür. "S" takısı (HTTPS) iletişimin şifreli ve güvenli (Secure) olduğunu belirtir.
* **Durumsuzluk (Stateless):** HTTP protokolü yapı gereği geçmişi hatırlamaz. Her istek bağımsızdır; sunucu önceki istekleri aklında tutmaz.
* **Oturum Yönetimi (Statefulness):** Siteler kimliğimizi veya giriş yaptığımızı unutmamak için tarayıcıda saklanan çerezleri (cookie) veya jetonları (token) kullanarak uygulama düzeyinde bu sorunu çözerler.

### Temel HTTP Metodları (Komutları)
Ana RFC belgelerinde 9 temel metot bulunur: `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD`, `OPTIONS`, `CONNECT`, `TRACE`.

#### GET Metodu
En yaygın kullanılan metottur. Bir web sunucusundan kaynak **almak/çekmek** için kullanılır. Bir tarayıcıya adres yazıldığında, tarayıcı arka planda sunucuya otomatik olarak bir GET isteği oluşturur.

### URL Yapısı ve Ağ İsteklerini İnceleme
Bir ağ isteğini tarayıcının Geliştirici Araçları (F12 -> Network sekmesi) üzerinden incelediğimizde bazı temel kavramlarla karşılaşırız:
* **Scheme (Şema/Protokol):** Kullanılan protokol (Örn: `https://`)
* **Host (Sunucu/Makine):** Kaynak talep edilen sunucunun adı (Örn: `www.iamlearning.thm`)
* **Path / Filename (Yol/Dosya Adı):** Sunucudan istenen dosya veya uzantı (Örn: `/contact` veya `index.html`)
* **Status (Durum Kodu):** İsteğin sonucu.
  * `200 OK`: İstek başarılı.
  * `500 Internal Server Error`: Sunucunun kendi iç işleyişinde meydana gelen beklenmedik bir hata (çökme, veritabanı sorunu vb.). Bu hata istemcinin değil, sunucunun sorunudur.

> **Not:** Bir sunucu yanıtı her zaman iki bölümden oluşur: **Yanıt başlığı** (meta veriler) ve **Yanıt gövdesi** (örneğin HTML kodları gibi asıl içerik).