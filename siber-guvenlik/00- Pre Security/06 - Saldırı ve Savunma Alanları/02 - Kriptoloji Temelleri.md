## 1. Temel Kriptografi Kavramları

* **Düz Metin (Plaintext):** Normal olarak okunabilen, şifrelenmemiş orijinal mesaj (Örn: `MERHABA`).
* **Şifreli Metin (Ciphertext):** Karıştırılmış, anahtar olmadan anlamsız görünen metin (Örn: `PHTKDED`).
* **Algoritma (Algorithm):** Verinin nasıl karıştırılacağını belirleyen herkese açık matematiksel yöntem veya kurallar dizisi (Örn: AES, RSA, Sezar Şifresi).
* **Anahtar (Key):** Algoritmanın kullandığı gizli parola/bileşen. Güvenlik algoritmanın gizliliğinden değil, **anahtarın gizliliğinden** gelir.

---

## 2. Şifreleme Türleri

### Simetrik Şifreleme (Symmetric Encryption)
Hem şifreleme hem de şifre çözme işlemleri için **aynı tek anahtar** kullanılır (Kilitli bir kutuyu aynı anahtarla kilitleyip açmak gibi).
* **Avantajları:** Çok hızlıdır, büyük verileri (dosyalar, sabit diskler, ağ trafiği) şifrelemek için idealdir.
* **Dezavantajı (Anahtar Dağıtımı Problemi):** İki taraf bu ortak anahtarı ilk başta güvenli bir şekilde nasıl paylaşacak? İnternet üzerinden düz metin gönderilirse ele geçirilebilir.
* **Örnek:** Sezar Şifresi (sadece eğitim amaçlıdır, zayıftır).

### Asimetrik Şifreleme (Asymmetric Encryption)
Matematiksel olarak birbirine bağlı **iki farklı anahtar** kullanır:
1. **Genel Anahtar (Public Key):** Herkesle açıkça paylaşılır. Sadece veri şifrelemek için kullanılır.
2. **Özel Anahtar (Private Key):** Asla paylaşılmaz, sadece sahibinde kalır. Genel anahtarla şifrelenen veriyi **sadece** bu anahtar çözebilir.
* **Avantajı:** Anahtar dağıtımı problemini çözer. Tarafların önceden ortak bir sır paylaşmasına gerek kalmaz. (Posta kutusu analojisi: Herkes posta atabilir, sadece anahtarı olan kutu sahibi postaları okuyabilir).
* **Dezavantajı:** Yavaş çalışır ve yoğun işlem gücü gerektirir.

---

## 3. Hibrit Yaklaşım (HTTPS Nasıl Çalışır?)

Gerçek dünyadaki modern sistemler (HTTPS, VPN, WhatsApp) hız ve güvenliği birleştirmek için ikisini aynı anda kullanır:

1. **Bağlantı Başlangıcı (El Sıkışma):** Tarayıcı ve sunucu, güvenli bir şekilde ortak bir simetrik anahtar belirlemek için **Asimetrik Şifreleme** kullanır.
2. **Veri Transferi (Oturum):** Ortak anahtar güvenle paylaşıldıktan sonra sistem çok daha hızlı olan **Simetrik Şifrelemeye** geçer ve bulk (yığın) veriler bu şekilde aktarılır.

### Dijital Sertifikalar (Digital Certificates)
Bir web sitesinin gönderdiği *Genel Anahtarın* gerçekten o siteye (örneğin google.com) ait olduğunu doğrulayan dijital kimliklerdir. **Sertifika Yetkilileri (CA - Certificate Authority)** tarafından imzalanırlar. Tarayıcınızdaki asma kilit simgesinin temelidir.

---

## 4. Karşılaştırma Özeti

| Özellik | Simetrik Şifreleme | Asimetrik Şifreleme |
| :--- | :--- | :--- |
| **Anahtar Sayısı** | 1 (Ortak Anahtar) | 2 (Genel ve Özel Anahtar) |
| **Anahtar Paylaşımı** | İki taraf da aynı anahtara sahip olmalı | Genel anahtar herkesle paylaşılabilir |
| **Hız** | Çok Hızlı | Yavaş |
| **Kullanım Alanı** | Büyük boyutlu verilerin ve ağ trafiğinin şifrelenmesi | Anahtar değişimi (güvenli paylaşım) ve dijital imzalar |
