
## 1. Temel Sistem Komutları

* **`whoami`**: Şu anda hangi kullanıcı olarak giriş yapıldığını gösterir.
* **`echo`**: Sağlanan metni ekrana bastırır.
  * *Örnek:* `echo "Hello Friend!"` (Birden fazla kelime/boşluk varsa çift tırnak kullanılır).
* **`pwd`** (*print working directory*): Bulunulan çalışma dizininin tam yolunu (path) gösterir.

---

## 2. Dosya Sistemi ile Etkileşim

* **`ls`** (*listing*): Bulunulan dizindeki dosya ve klasörleri listeler.
  * *İpucu:* Dizine gitmeden listelemek için `ls KlasorAdi` kullanılabilir.
* **`cd`** (*change directory*): Belirtilen dizine geçiş yapar (Örn: `cd Pictures`).
* **`cat`** (*concatenate*): Dosyaların içeriğini terminale yazdırır (Metin dosyaları, şifreler, bayraklar vb.).
  * *İpucu:* `cat /yol/dosya.txt` şeklinde dizin değiştirmeden de okunabilir.

---

## 3. Gelişmiş Arama Komutları (`find` ve `grep`)

### `find` (Dosya Arama)
Sistem genelinde veya mevcut dizinde dosya/klasör aramak için kullanılır.
* **İsme göre arama:** `find -name passwords.txt`
* **Joker karakter ile arama:** `find -name *.txt` (Tüm `.txt` uzantılı dosyaları bulur).

### `grep` (İçerik Arama)
Dosyaların *içinde* belirli kelimeleri, IP adreslerini veya değerleri arar.
* **Dosya içinde arama:** `grep "81.143.211.90" access.log`
* **Özyineli (Recursive) Arama:** `grep -R "PRETTY_NAME" /etc/` (Belirtilen dizindeki ve alt klasörlerdeki tüm dosyalarda arama yapar).

---

## 4. Kabuk Operatörleri (Shell Operators)

Komutların akışını yönetmek ve otomatikleştirmek için kullanılan temel operatörler:

* **`&` (Arka Planda Çalıştırma):** Uzun süren komutların terminali meşgul etmeden arka planda çalışmasını sağlar.
* **`&&` (Komut Birleştirme):** Birden fazla komutu ardarda ekler. *Kural:* `komut1 && komut2` yazıldığında, yalnızca `komut1` başarılı olursa `komut2` çalışır.
* **`>` (Çıktı Yönlendirici - Overwrite):** Bir komutun çıktısını alıp bir dosyaya yazdırır. Eğer dosya varsa **içeriğinin üzerine yazar** (eski veriler silinir).
  * *Örnek:* `echo hey > welcome`
* **`>>` (Çıktı Ekleme - Append):** Çıktıyı dosyanın üzerine yazmak yerine **en sonuna ekler** (hiçbir veri silinmez).
  * *Örnek:* `echo hello >> welcome`