# Ağ Teknolojileri ve İnternet Temelleri

## 1. Ağ (Network) Kavramı ve Günlük Hayat
Ağlar, en basit tanımıyla birbirine bağlı olan varlıklar veya nesnelerdir. Günlük hayatın her alanında ağ yapılarıyla karşılaşmak mümkündür:
- **Sosyal Ağlar:** Benzer ilgi alanları, hobiler ve becerilerle birbirine bağlanan arkadaş çevreleri.
- **Altyapı ve Sistemler:** Bir şehrin toplu taşıma sistemi, ulusal elektrik şebekesi, posta ve kargo dağıtım sistemleri.

### Bilişimde Ağ Yapısı
Bilişim dünyasında ağ oluşturma (networking), aynı mantığın teknolojik cihazlara uyarlanmış halidir. 
- Bir ağ; dizüstü bilgisayarlar, telefonlar, güvenlik kameraları, trafik ışıkları ve hatta akıllı tarım cihazları dahil olmak üzere **2 cihazdan milyarlarca cihaza kadar** genişleyebilir.
- Veri toplama, kaynak paylaşımı ve siber güvenlik süreçlerinin yönetilmesi tamamen ağ altyapılarına bağlıdır. Bu nedenle siber güvenlikte ağ mantığını kavramak temel bir zorunluluktur.

---

## 2. İnternet ve Tarihçesi
İnternet, kendi içinde çok sayıda küçük ağı barındıran devasa bir küresel ağdır.

### Tarihsel Gelişim Kronolojisi
- **1960'ların Sonu (ARPANET):** ABD Savunma Bakanlığı tarafından finanse edilen bu proje, işler haldeki ilk belgelenmiş bilgisayar ağıdır. İnternet'in ilk sürümü olarak kabul edilir.
- **1989 (World Wide Web - WWW):** Tim Berners-Lee tarafından WWW'nin yaratılmasıyla bildiğimiz anlamda İnternet icat edilmiştir. Bu kırılma noktasından sonra İnternet, bilgi depolama ve paylaşım havuzu haline gelmiştir.

---

## 3. Ağ Türleri
Ağlar genel olarak iki ana kategoriye ayrılır:

1. **Özel Ağ (Private Network):** Evinizdeki, okulunuzdaki veya iş yerinizdeki yerel cihazların kendi arasında iletişim kurduğu kapalı ağlardır.
2. **Genel Ağ (Public Network):** Bu küçük özel ağları birbirine bağlayan, dış dünyaya açık olan büyük ağdır (yani İnternet'in kendisi).

---

## 4. Cihaz Kimliklendirme Sistemleri
Cihazların bir ağ üzerinde düzen içinde iletişim kurabilmesi için hem kendilerini tanıtabilmesi hem de diğerleri tarafından tanımlanabilmesi gerekir. Bunun için iki temel adresleme yöntemi kullanılır:

### A. IP Adresi (Internet Protocol Address)
IP adresi, ağdaki bir cihazı belirli bir süre boyunca tanımlamak için kullanılan dinamik veya statik bir etikettir. 4 oktete (sekizli gruba) bölünmüş sayılardan oluşur (Örn: `192.168.1.1`). Aynı ağ içinde aynı anda birden fazla cihazda aynı IP adresi aktif olamaz.

IP adresleri bulundukları ağ türüne göre ikiye ayrılır:
- **Özel IP (Private IP):** Yerel ağdaki cihazların birbirini tanıması için kullanılır. (Örn: `192.168.1.77`)
- **Genel IP (Public IP):** Cihazın İnternet dünyasında tanınmasını sağlar. İnternet Servis Sağlayıcınız (ISS) tarafından atanır. Yerel ağdaki tüm cihazlar dış dünyaya aynı Genel IP üzerinden çıkış yapar.

#### IP Sürümleri (IPv4 vs IPv6)
- **IPv4:** 2^32 adet (yaklaşık 4.29 milyar) benzersiz adres sunar. Günümüzde bağlanan cihaz sayısının aşırı artması nedeniyle adres kıtlığı yaşanmaktadır.
- **IPv6:** Adres kıtlığı sorununu çözmek için geliştirilen yeni nesil şemadır. 2^128 adet (340 trilyondan fazla) benzersiz adres destekler ve yeni metodolojileri sayesinde daha verimlidir.

### B. MAC Adresi (Media Access Control Address)
Cihazın anakartında yer alan fiziksel ağ arayüzüne (Network Interface), üretildiği fabrikada atanan benzersiz bir donanım adresidir. Bir nevi cihazın parmak izidir.
- **Biçimi:** İkişerli gruplar halinde, iki nokta üst üste ile ayrılmış 12 karakterli onaltılık (hexadecimal) bir sayıdır. (Örn: `a4:c3:f0:85:ac:2d`)
- İlk 6 karakter üretici firmayı (OUI), son 6 karakter ise karta ait benzersiz numarayı temsil eder.

> [!WARNING] MAC Spoofing (MAC Sahteciliği)
> MAC adresleri yazılımsal olarak taklit edilebilir veya değiştirilebilir. Saldırganlar, ağdaki yetkili bir kullanıcının (örneğin ağ yöneticisinin) MAC adresini kopyalayarak zayıf yapılandırılmış güvenlik duvarlarını veya kafe/otel gibi yerlerdeki misafir Wi-Fi kimlik doğrulama sistemlerini (Captive Portal) atlatabilirler.

---

## 5. Temel Ağ Teşhis Araçları: Ping
Ping, iki cihaz arasındaki bağlantının durumunu ve kalitesini ölçmek amacıyla kullanılan en temel ağ aracıdır. Windows, Linux ve macOS gibi modern tüm işletim sistemlerinde yerleşik olarak gelir.

- **Çalışma Mantığı:** Hedef cihaza **ICMP (Internet Control Message Protocol)** protokolüne ait bir "yankı (echo)" paketi gönderir. Hedef cihaz çalışır durumdaysa "yankı yanıtı (echo reply)" döner.
- **Ölçüm:** Paketlerin gidip gelme süresi (milisaniye - ms cinsinden) ölçülerek bağlantının kararlılığı ve hızı test edilir.
- **Kullanım Sözdizimi:**

```bash
ping [IP_Adresi_veya_Web_Sitesi_URLsi]
# Örnekler:
ping 192.168.1.254
ping 8.8.8.8
ping google.com
```
