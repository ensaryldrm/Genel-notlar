## 1. DNS (Domain Name System) Nedir?
DNS, internet üzerindeki cihazlarla karmaşık IP adreslerini ezberlemek zorunda kalmadan iletişim kurmamızı sağlayan "internet telefon rehberi" sistemidir.
- Her bilgisayarın ve sunucunun `104.26.10.229` formatında benzersiz bir IP adresi vardır.
- DNS, bu karmaşık IP adreslerini akılda kalıcı alan adlarına (Örn: `tryhackme.com`) çevirerek internet kullanımını kolaylaştırır.

---

## 2. Alan Adı Hiyerarşisi (Domain Hierarchy)
Bir web sitesi adresi (alan adı) rastgele oluşturulmaz; sağdan sola doğru okunan belirli bir yapıya sahiptir.

### Üst Düzey Alan Adı (TLD - Top-Level Domain)
Bir alan adının en sağında bulunan kısımdır. (Örn: `tryhackme.com` adresindeki **`.com`**) İki türe ayrılır:
- **gTLD (Genel):** Alan adının amacını belirtir (`.com` ticari, `.org` organizasyon, `.edu` eğitim, `.online` vb.).
- **ccTLD (Ülke Kodu):** Coğrafi aidiyet belirtir (`.tr` Türkiye, `.uk` Birleşik Krallık vb.).

### İkinci Düzey Alan Adı (Second-Level Domain)
Alan adının asıl marka/isim kısmıdır. (Örn: `tryhackme.com` adresindeki **`tryhackme`**).
- Maksimum 63 karakter olabilir. Sadece harf, rakam ve tire içerebilir (tire ile başlayıp bitemez).

### Alt Alan Adı (Subdomain)
İkinci düzey alan adının solunda yer alan ve noktayla ayrılan alt bölümlerdir. (Örn: `admin.tryhackme.com` adresindeki **`admin`**).
- İstenildiği kadar alt alan adı eklenebilir, ancak tüm web adresinin toplam uzunluğu **253 karakteri** geçemez.

---

## 3. Temel DNS Kayıt Türleri
DNS sadece siteleri açmak için değil, e-posta ve doğrulama gibi birçok işlem için farklı kayıt türleri tutar:

- **A Kaydı (A Record):** Alan adını bir **IPv4** adresine yönlendirir. (Örn: `104.26.10.229`)
- **AAAA Kaydı:** Alan adını bir **IPv6** adresine yönlendirir. (Örn: `2606:4700:20::681a:be5`)
- **CNAME Kaydı:** Alan adını başka bir alan adına yönlendirir (Alias/Takma ad). IP'yi bulmak için o yeni alan adına tekrar DNS sorgusu yapılır.
- **MX Kaydı (Mail Exchange):** O alan adına gelen e-postaları yönetecek posta sunucularının adresini ve öncelik sırasını tutar.
- **TXT Kaydı:** Serbest metin alanıdır. Genellikle spam e-postaları önlemek (SPF, DMARC) veya domain sahipliğini doğrulamak için kullanılır.

---

## 4. Adım Adım DNS İstek Süreci (DNS Çözümleme)
Tarayıcıya bir adres (Örn: `tryhackme.com`) yazıldığında, IP adresini bulmak için arka planda sırasıyla şu adımlar gerçekleşir:

1. **Yerel Önbellek (Local Cache):** Bilgisayarınız adresi önce kendi hafızasında (önbellek) arar. Bulursa işlem biter ve site açılır.
2. **Özyineli DNS Sunucusu (Recursive DNS Server):** Bilgisayarda yoksa istek genellikle İSS'nizin (veya Google DNS gibi) sağladığı sunucuya gider. Bu sunucu kendi önbelleğine bakar.
3. **Kök DNS Sunucusu (Root DNS Server):** İnternetin omurgasıdır. Aradığınız adresin uzantısına (`.com`) bakarak sizi doğru TLD sunucusuna yönlendirir.
4. **TLD Sunucusu:** Aradığınız alan adının asıl kayıtlarını barındıran Yetkili Sunucunun adresini bilir ve isteği oraya iletir.
5. **Yetkili Sunucu (Authoritative Nameserver):** Alan adına ait tüm asıl DNS kayıtlarının (A, MX vb.) tutulduğu yerdir. İsteğin kesin cevabı (IP adresi) buradan alınır.

> [!tip] TTL (Time To Live - Yaşam Süresi)
> Yetkili sunucudan dönen IP adresi yanıtı, bilgisayarınızda ve Özyineli sunucuda **TTL değeri** (saniye cinsinden) kadar önbellekte saklanır. Böylece siteye her girişinizde bu uzun sorgulama işlemi tekrar edilmez, internet trafiği rahatlar.