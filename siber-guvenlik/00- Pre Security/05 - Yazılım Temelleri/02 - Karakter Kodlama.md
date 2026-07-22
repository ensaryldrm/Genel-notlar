## 1. ASCII (American Standard Code for Information Interchange)

İngilizce harfler için oluşturulan en eski standartlardan biridir.
* **7 bitlik** bir standarttır.
* Toplam **128 karakteri** (İngilizce büyük/küçük harfler, rakamlar, temel noktalama işaretleri ve kontrol karakterleri) kapsar.
* *Örnek:* "A" harfinin ondalık (decimal) karşılığı `65`, onaltılık (hex) karşılığı `41`, ikili (binary) karşılığı ise `01000001`'dir.
* **Sınırlılıkları:** `ñ`, `ş`, `ğ`, `€` gibi diğer dillerdeki özel karakterleri barındıracak kapasitesi yoktur.

---

## 2. Genişletilmiş ASCII (Extended ASCII) ve Kodlama Kaosu

ASCII'nin yetersiz kalması üzerine 8. bit eklenerek 128 karakterlik daha yer açıldı (ISO-8859 serisi).
* **ISO-8859-1 (Latin-1):** Batı Avrupa dilleri.
* **ISO-8859-2 (Latin-2):** Orta/Doğu Avrupa dilleri.
* **Kaosun Nedeni:** Bir belge ISO-8859-1 ile kaydedilip ISO-8859-2 ile açılırsa karakterler yanlış eşleşir (Örn: `Ø` harfinin `Ř` olarak görünmesi). Binlerce karakter içeren Asya dilleri ve emojiler için bu sistem tamamen yetersizdir.

---

## 3. Unicode: Evrensel Karakter Seti

Tüm dillerdeki tüm karakterleri (ve emojileri) tek bir standartta toplamak için geliştirilmiştir.
* Her karaktere benzersiz bir "kod noktası (code point)" atar. Hangi dili kullandığınızı seçme zorunluluğunu ortadan kaldırır.
* *Örnekler:*
  * `U+0041` = Latin "A"
  * `U+03A9` = Yunan "Ω"
  * `U+1F60A` = 😊 (Gülen yüz emojisi)

---

## 4. UTF (Unicode Transformation Format) Standartları

Unicode kod noktalarının bellekte kaç baytlık (byte) yer kaplayacağını ve nasıl saklanacağını belirleyen standartlardır.

### UTF-8
Modern web'de en yaygın kullanılan kodlamadır. **Dinamik** bir yapıya sahiptir; karakterin karmaşıklığına göre **1 ila 4 bayt** arasında yer kullanır.
* **Avantajı:** Standart ASCII karakterleri için tıpkı eski sistemdeki gibi 1 bayt kullanır. Bu sayede eski sistemlerle (ASCII) %100 geriye dönük uyumluluk sağlar.
* Emojiler (Örn: 🔥) için 4 bayt kullanır. Bellek israfını önler.

### UTF-16
Karakter başına **2 veya 4 bayt** kullanır.
* Çoğu yaygın karakter (Latin, Kiril, Çince) 2 bayta sığar.
* Emojiler ve çok nadir alfabeler 4 bayt gerektirir.

### UTF-32
Sabit uzunlukludur. Her karakter (ister 'A' harfi olsun, ister bir emoji) istisnasız **4 bayt** kullanır.
* İşlenmesi en basit olanıdır ancak en çok bellek israfı yapan formattır.