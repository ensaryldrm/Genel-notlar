## 1. Temel Sayı Sistemleri

* **Ondalık (Decimal - 10 Tabanlı):** Günlük hayatımızda kullandığımız standart sayı sistemidir (0-9 arası rakamlar).
* **İkili (Binary - 2 Tabanlı):** Bilgisayarların anladığı temel dildir. Sadece **0 ve 1** durumlarını kullanır.
* **Onaltılık (Hexadecimal - 16 Tabanlı):** Uzun ikili sayıları daha okunabilir kılmak için her 4 bitlik grubu tek bir karakterde birleştirir.
  * Rakamlar: `0-9` ve `A-F` (A=10, B=11, C=12, D=13, E=14, F=15).
* **Sekizlik (Octal - 8 Tabanlı):** Her 3 bitlik grubu tek bir karakterde birleştirir (0-7 arası rakamlar). Modern sistemlerde daha az rastlanır.

---

## 2. Veri ve Renk Ölçü Birimleri

Bilgisayarlar renkleri Kırmızı, Yeşil ve Mavi (RGB) ışıklarının karışımı olarak işler.

* **Bit (Binary Digit):** Bir bilgisayardaki en küçük veri birimidir. Sadece `0` veya `1` olabilir.
* **Bayt (Byte / Octet):** 8 bitin bir araya gelmesiyle oluşan veri grubudur. 1 Bayt, $2^8 = 256$ farklı durumu temsil edebilir.
* **Hex (Onaltılık) Renk Kodları:** Modern bilgisayar sistemlerinde (24-bit renk derinliği), her bir ana renk (Kırmızı, Yeşil, Mavi) için 1'er Bayt ayrılır. 
  * Bu sayede $256 \times 256 \times 256 = 16.777.216$ (yaklaşık 16 milyon) renk kombinasyonu elde edilir.
  * İkili sayıları okumak zor olduğu için renkler Hex formatında yazılır (Örn: İkili sistemdeki `10100011 11101010 00101010` yerine Hex sisteminde `A3EA2A` yazılır).

---

## 3. İkili Sistem (Binary) Hesaplama Mantığı

İkili sistemdeki bir sayıyı ondalık sisteme çevirirken, tıpkı ondalık sistemdeki birler, onlar, yüzler basamağı gibi sağdan sola doğru 2'nin kuvvetleri ($2^0, 2^1, 2^2, 2^3...$) ile çarpım yapılır.

### Dönüştürme Örnekleri

**Örnek 1:** `1001` (Binary) sayısının ondalık karşılığı:
$$1001 = (1 \times 2^3) + (0 \times 2^2) + (0 \times 2^1) + (1 \times 2^0)$$
$$1001 = 8 + 0 + 0 + 1 = 9$$

**Örnek 2:** `1111` (Binary) sayısının ondalık karşılığı:
$$1111 = (1 \times 2^3) + (1 \times 2^2) + (1 \times 2^1) + (1 \times 2^0)$$
$$1111 = 8 + 4 + 2 + 1 = 15$$