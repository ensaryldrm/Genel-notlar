# Web İletişimi: HTTP, URL'ler ve Çerezler

## 1. HTTP ve HTTPS
Web sayfalarının (HTML, resim, video vb.) sunucu ile istemci (tarayıcı) arasında nasıl iletileceğini belirleyen kurallar bütünüdür.
- **HTTP (Hiper Metin Aktarım Protokolü):** Veriler düz metin olarak iletilir, şifreleme yoktur.
- **HTTPS (Güvenli HTTP):** İletişim tamamen şifrelenir. Araya girenlerin verileri okumasını engeller ve doğru sunucuya bağlandığınızı doğrular.

---

## 2. URL (Tekdüze Kaynak Bulucu) Yapısı
İnternetteki bir kaynağa (web sayfası, dosya vb.) nasıl ve nereden erişileceğini belirten talimatlardır. Tam bir URL şu bileşenlerden oluşabilir:

- **Şema (Scheme):** Kullanılacak protokolü belirtir. (`http://`, `https://`, `ftp://`)
- **Kullanıcı (User):** Kimlik doğrulama gerektiren yerlerde kullanıcı adı/şifre.
- **Ana Bilgisayar (Host):** Sunucunun IP adresi veya alan adı. (Örn: `tryhackme.com`)
- **Port:** Bağlanılacak kapı numarası. (Varsayılan: HTTP için `80`, HTTPS için `443`)
- **Yol (Path):** Sunucudaki kaynağın veya dosyanın konumu. (Örn: `/blog`)
- **Sorgu Dizesi (Query String):** Sunucuya gönderilen ekstra parametrelerdir. `?` ile başlar. (Örn: `?id=1`)
- **Parça (Fragment):** Sayfa içindeki belirli bir başlığa/bölüme doğrudan gitmek için kullanılır. `#` ile başlar.

---

## 3. HTTP Metotları
İstemcinin (tarayıcının) sunucudan ne tür bir işlem yapmasını istediğini belirten komutlardır.

- **GET:** Sunucudan sadece veri okumak/çekmek için kullanılır.
- **POST:** Sunucuya veri göndermek veya yeni bir kayıt oluşturmak için kullanılır.
- **PUT:** Sunucudaki mevcut bir veriyi güncellemek için kullanılır.
- **DELETE:** Sunucudaki bir veriyi/kaydı silmek için kullanılır.

---

## 4. HTTP İstek ve Yanıt (Request & Response) Mimarisi

### Örnek Bir HTTP İsteği (Request)
Tarayıcı sunucuya şu formatta bir metin bloğu gönderir:
```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: [https://tryhackme.com/](https://tryhackme.com/)

````

- **Satır 1:** Kullanılan metot (GET), istenen yol (/) ve protokol sürümü (HTTP/1.1).
    
- **Satır 2-4:** Ekstra bilgileri taşıyan başlıklar (Headers).
    
- **Boş Satır:** İsteğin bittiğini sunucuya bildirmek için her zaman boş bir satırla biter.
    

### Örnek Bir HTTP Yanıtı (Response)

Sunucu isteği işler ve şu formatta geri döndürür:

```HTTP
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html 
Content-Length: 98

<html>...</html>
```
- **Satır 1:** Protokol sürümü (HTTP/1.1) ve işlemin sonucunu belirten Durum Kodu (200 OK).
    
- **Satır 2-5:** Gönderilen verinin türü ve boyutunu belirten başlıklar.
    
- **Boş Satır:** Başlıkların bittiğini belirtir. Altındaki kısım talep edilen asıl veridir (HTML kodları).
    

## 5. HTTP Durum Kodları (Status Codes)

Sunucunun, yapılan isteğin sonucunu istemciye bildirdiği 3 haneli numaralardır.

### Durum Kodu Aralıkları

- **100-199 (Bilgi):** İstek alındı, işlem devam ediyor.
    
- **200-299 (Başarı):** İstek başarıyla anlaşıldı ve kabul edildi.
    
- **300-399 (Yönlendirme):** İsteği tamamlamak için farklı bir adrese gitmek gerekiyor.
    
- **400-499 (İstemci Hatası):** İstekte hata var (Yanlış URL, yetkisiz erişim vb.).
    
- **500-599 (Sunucu Hatası):** İstek geçerli ama sunucu tarafında bir çökme/hata oluştu.
    

### Sık Karşılaşılan Durum Kodları

| **Kod** | **İsim**              | **Açıklama**                                                               |
| ------- | --------------------- | -------------------------------------------------------------------------- |
| **200** | OK                    | İşlem başarılı.                                                            |
| **201** | Created               | İstek başarılı ve yeni bir kaynak oluşturuldu.                             |
| **301** | Moved Permanently     | Sayfa kalıcı olarak başka bir adrese taşındı.                              |
| **302** | Found                 | Sayfa geçici olarak başka bir adrese yönlendirildi.                        |
| **400** | Bad Request           | Gönderilen istek hatalı veya parametreler eksik.                           |
| **401** | Not Authorised        | Kaynağa erişmek için sisteme giriş (login) yapmalısınız.                   |
| **403** | Forbidden             | Giriş yapmış olsanız bile bu kaynağı görme yetkiniz yok.                   |
| **404** | Page Not Found        | İstenen sayfa/kaynak sunucuda bulunamadı.                                  |
| **405** | Method Not Allowed    | İstenen kaynak bu metodu desteklemiyor (Örn: POST beklerken GET atılması). |
| **500** | Internal Server Error | Sunucu kaynaklı iç hata.                                                   |
| **503** | Service Unavailable   | Sunucu şu an aşırı yüklü veya bakımda.                                     |
## 6. HTTP Başlıkları (Headers)

İletişim sırasında meta verilerin (tarayıcı tipi, veri boyutu, çerezler vb.) taşındığı satırlardır.

### Yaygın İstek (Request) Başlıkları

- **Host:** İstenen sitenin alan adı. (Aynı sunucudaki farklı siteleri ayırmak için kritiktir).
    
- **User-Agent:** Tarayıcınızın ve işletim sisteminizin bilgisidir.
    
- **Content-Length:** POST/PUT işlemlerinde gönderilen verinin boyutunu belirtir.
    
- **Accept-Encoding:** Tarayıcının desteklediği sıkıştırma formatlarını (gzip vb.) sunucuya bildirir.
    
- **Cookie:** Sunucuya kim olduğunuzu hatırlatmak için gönderilen oturum verileridir.
    

### Yaygın Yanıt (Response) Başlıkları

- **Set-Cookie:** Sunucunun, tarayıcınıza kaydetmesi için gönderdiği yeni çerez bilgileridir.
    
- **Cache-Control:** Gelen verinin tarayıcı önbelleğinde ne kadar süre tutulacağını belirler.
    
- **Content-Type:** Dönen verinin formatını belirtir (Örn: `text/html`, `image/png`).
    
- **Content-Encoding:** Verinin internette yollanırken hangi yöntemle sıkıştırıldığını belirtir.
    

## 7. Çerezler (Cookies)

HTTP **durumsuz (stateless)** bir protokoldür; yani sizin önceki sayfalarda ne yaptığınızı veya sisteme giriş yapıp yapmadığınızı hatırlamaz.

Bu sorunu çözmek için **Çerezler** kullanılır:

- Sunucu size bir kereye mahsus `Set-Cookie` başlığı ile bir "token" (benzersiz şifreli metin) gönderir.
    
- Tarayıcınız bu çerezi kaydeder ve sonraki her site içi tıklamanızda (istekte) `Cookie` başlığı altında sunucuya geri yollar.
    
- Sunucu bu çereze bakarak sizi tanır ve oturumunuzu açık tutar.
    

> [!tip] Çerezleri Görüntüleme Tarayıcınızın **Geliştirici Araçları (F12) -> Ağ (Network)** sekmesinden yapılan istekleri ve gönderilen/alınan tüm çerezleri detaylıca inceleyebilirsiniz.