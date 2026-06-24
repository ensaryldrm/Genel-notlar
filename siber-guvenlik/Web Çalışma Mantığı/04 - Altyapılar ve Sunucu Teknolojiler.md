# Web Altyapısı ve Sunucu Teknolojileri

## 1. Web İletişimi (Özet)
Bir web sitesine girmek istediğinizde arka planda sırasıyla şunlar gerçekleşir:
1. Bilgisayarınız hedef sunucunun IP adresini bulmak için **DNS** kullanır.
2. Bilgisayarınız, IP'sini bulduğu sunucuyla **HTTP/HTTPS** protokolünü kullanarak iletişim kurar.
3. Web sunucusu size sitenin HTML, CSS, JS ve resim dosyalarını gönderir.
4. Tarayıcınız (Ön Uç / Frontend) bu verileri derleyip (render) siteyi ekranda gösterir.

---

## 2. Gelişmiş Web Bileşenleri

### Yük Dengeleyiciler (Load Balancers)
Yüksek trafikli sitelerde gelen istekleri tek bir sunucu yerine, arka planda çalışan birden fazla sunucuya dengeli bir şekilde dağıtan sistemlerdir.
- **Dağıtım Algoritmaları:** İstekleri sırayla dağıtabilir (*Round-robin*) veya en az meşgul olan sunucuya yönlendirebilir (*Weighted*).
- **Sağlık Kontrolü (Health Check):** Sunucuların çöküp çökmediğini periyodik olarak kontrol eder. Bir sunucu çökerse ona trafik göndermeyi keser (Failover) ve siteyi açık tutar.

### CDN (İçerik Dağıtım Ağları)
Web sitesinin statik dosyalarını (JavaScript, CSS, Resim, Video) dünyanın farklı yerlerindeki binlerce sunucuda kopyalayarak barındıran sistemdir. Kullanıcıya fiziksel olarak en yakın sunucudan dosyaları göndererek sitenin yüklenme hızını artırır ve ana sunucunun bant genişliği yükünü hafifletir.

### Veritabanları (Databases)
Kullanıcı bilgilerini, şifreleri, site içi gönderileri ve ayarları saklamak/geri çağırmak için kullanılır. En yaygın olanları: MySQL, MSSQL, MongoDB ve Postgres'tir.

### WAF (Web Uygulaması Güvenlik Duvarı)
Kullanıcı (istemci) ile web sunucusu arasında konumlanarak sunucuyu hack girişimlerinden ve DDoS (hizmet reddi) saldırılarından korur.
- Gelen HTTP isteklerinin bir bottan mı yoksa gerçek bir tarayıcıdan mı geldiğini analiz eder. Zararlı istekleri (Örn: SQL/HTML Injection) sunucuya ulaşmadan düşürür (Drop).
- **Hız Sınırlaması (Rate Limiting):** Bir IP adresinden saniyede gelebilecek maksimum istek sayısını sınırlandırarak sunucunun aşırı yüklenmesini engeller.

---

## 3. Web Sunucuları ve Çalışma Mantığı

### Web Sunucusu (Web Server) Nedir?
Gelen HTTP bağlantılarını dinleyen ve kullanıcılara web içeriğini (sayfaları) ulaştıran arka plan yazılımlarıdır. En bilinenleri **Apache, Nginx, IIS ve NodeJS**'dir.
- Dosyaları genellikle **Kök Dizin (Root Directory)** adı verilen bir klasörden sunarlar. (Linux için genellikle `/var/www/html`, Windows IIS için `C:\inetpub\wwwroot`).

### Sanal Sunucular (Virtual Hosts)
Tek bir fiziksel web sunucusunun içinde **birden fazla farklı web sitesini (alan adını)** barındırmayı sağlayan yapılandırma dosyalarıdır.
- Gelen isteğin HTTP `Host` başlığına (Örn: `tryhackme.com` mu yoksa `example.com` mu) bakarak, isteği sunucu içindeki doğru klasöre (örneğin `/var/www/site_bir` veya `/var/www/site_iki`) yönlendirirler. Bu sayede bir sunucuda sınırsız site barındırılabilir.

---

## 4. İçerik Türleri ve Arka Uç (Backend)

### Statik vs Dinamik İçerik
- **Statik İçerik:** Herkese her zaman aynı görünen, değişmeyen HTML, CSS, JS ve medya dosyalarıdır.
- **Dinamik İçerik:** Kullanıcıya, veritabanına veya yapılan aramaya göre anlık olarak değişen içeriklerdir (Örn: Blogdaki son yazılar, e-ticaret sepetiniz).

### Arka Uç (Backend) ve Betik Dilleri
Dinamik içerikler, programlama dilleri kullanılarak **Arka Uç (Backend)** adı verilen ve kullanıcının göremediği kapalı bir alanda işlenir.
- **Popüler Diller:** PHP, Python, Ruby, NodeJS, Perl.
- **Görevi:** Veritabanlarıyla iletişim kurar, mantıksal hesaplamaları yapar ve sonucunu saf bir HTML sayfası olarak Ön Uca (Frontend) gönderir.
- **Güvenlik Notu:** Tarayıcıda "Sayfa Kaynağını Görüntüle" derseniz bu Backend kodlarını (Örn: PHP) asla göremezsiniz; sadece o kodların çalıştıktan sonra ürettiği HTML çıktısını görürsünüz. Etkileşimi sağlayan kısım burası olduğu için güvenlik açıklarının büyük bir kısmı backend dillerinin yanlış yapılandırılmasından kaynaklanır.