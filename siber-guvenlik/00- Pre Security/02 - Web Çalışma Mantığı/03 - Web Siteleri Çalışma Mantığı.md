# Web Geliştirme Temelleri ve Güvenlik

## 1. Web Sitelerinin Çalışma Mantığı
Bir web sitesi temelde iki ana bileşenin iletişim kurmasıyla çalışır:
- **Ön Uç (Front End / İstemci Tarafı):** Tarayıcınızın kodu yorumlayıp (render) web sitesini görsel olarak size sunduğu kısımdır.
- **Arka Uç (Back End / Sunucu Tarafı):** Sizin tarayıcıdan gönderdiğiniz istekleri işleyen ve bir yanıt (sayfa verisi) döndüren uzaktaki bilgisayardır (sunucudur).

---

## 2. Web Sitelerini Oluşturan Temel Teknolojiler
Web siteleri temel olarak üç ana yapı taşı kullanılarak inşa edilir: HTML (İskelet), CSS (Makyaj/Stil) ve JavaScript (Kas/Hareket).

### HTML (Hiper Metin İşaretleme Dili)
Web sitelerinin iskeletini ve yapısını tanımlar. **Öğeler (elements)** veya **etiketler (tags)** kullanılarak yazılır.
- `<!DOCTYPE html>`: Belgenin güncel HTML5 formatında olduğunu belirtir.
- `<html>`: Kök öğedir. Tüm sayfa kodları bunun içinde yer alır.
- `<head>`: Sayfa başlığı (sekme adı) gibi arka planda çalışan meta bilgileri içerir.
- `<body>`: Sitenin sadece ekranda görünen kısmını (gövdesini) kapsar.
- `<h1>`, `<p>`, `<button>`, `<img>`: Sırasıyla ana başlık, paragraf, buton ve resim gibi yapı taşlarını oluşturur.

**Nitelikler (Attributes):** Etiketlere ekstra özellik veya kimlik kazandırmak için etiketlerin içine yazılırlar.
- `class`: Birden fazla öğeye aynı şekillendirmeyi (CSS) atamak için kullanılır. (Örn: `<p class="kalin-metin">`)
- `id`: Sadece tek bir öğeye özgü, benzersiz bir kimliktir. JS ile o öğeyi bulmak için kritik öneme sahiptir. (Örn: `<p id="ozel-paragraf">`)
- `src`: Resim veya script gibi dış dosyaların konumunu belirtir. (Örn: `<img src="kedi.jpg">`)

> [!info] Kaynak Kodu Görüntüleme
> Tarayıcıda herhangi bir sayfaya sağ tıklayıp "Sayfa Kaynağını Görüntüle" diyerek o sitenin iskeletini (HTML kodlarını) olduğu gibi görebilirsiniz.

### JavaScript (JS)
Web sitelerini statik (sabit) olmaktan çıkarıp **etkileşimli (interaktif)** hale getirir.
- Sayfa yenilenmeden gerçek zamanlı dinamik güncellemeler yapabilir.
- Butona tıklama (`onclick`), fareyle üzerine gelme (`onhover`) gibi **olayları (events)** dinler ve buna göre tepki verir.
- Sayfaya `<script>` etiketleri arasında veya dışarıdan `src` niteliği ile dosya olarak (`.js`) eklenebilir.

---

## 3. Temel Web Güvenlik Açıkları
Web uygulamalarını test ederken (siber güvenlik bağlamında) ilk bakılan istemci taraflı (client-side) zafiyetler şunlardır:

### Hassas Veri İfşası (Sensitive Data Exposure)
Geliştiricilerin sitenin kaynak kodunda unutmaması gereken gizli verileri açıkça bırakması durumudur.
- **Nasıl Oluşur?:** Sayfa kaynağındaki HTML veya JS kodları arasına yazılmış yorum satırlarında geçici şifrelerin, API anahtarlarının veya gizli yönetici bağlantılarının düz metin (clear-text) olarak unutulmasıyla oluşur.
- **Tehlikesi:** Saldırganlar sadece "Sayfa Kaynağını Görüntüle" diyerek bu bilgileri toplayabilir ve sistemde yetkisiz erişim sağlayabilir.

### HTML Enjeksiyonu (HTML Injection)
Kullanıcının girdiği verilerin (input) site tarafından temizlenmeden (sanitize edilmeden) doğrudan ekranda çalıştırılmasıyla oluşan bir zafiyettir.
- **Nasıl Oluşur?:** Sitedeki bir yorum alanına veya adınızı soran bir forma normal bir metin yerine `<h1>Hacklendi</h1>` gibi bir HTML etiketi yazıp gönderdiğinizde, sistem bunu ekranda kocaman bir başlık olarak render ediyorsa sistemde HTML Enjeksiyonu açığı vardır.
- **Çözüm (Altın Kural):** Kullanıcı girdisine (user input) **asla** güvenilmemelidir. Gelen her veri, ekrana basılmadan önce mutlaka "sanitize" edilmeli (tehlikeli HTML ve JS etiketlerinden arındırılmalı) ve filtrelenmelidir.