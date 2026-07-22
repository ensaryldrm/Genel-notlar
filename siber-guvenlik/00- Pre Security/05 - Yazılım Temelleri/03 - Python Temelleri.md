## Temel Programlama Kavramları

Bu notta, programlama dillerinin üç temel yapı taşı ele alınmıştır:

* **Değişkenler (Variables):** Verileri bellekte tutmak için kullanılan isimlendirilmiş alanlardır (Örn: `secret`, `tries`, `guess`).
* **Koşullu İfadeler (Conditionals):** Karar verme mekanizmalarıdır. Belirli bir koşulun doğru (true) veya yanlış (false) olmasına göre farklı kod bloklarının çalışmasını sağlarlar (`if`, `elif`, `else`).
* **Döngüler (Loops / Iterations):** Belirli bir koşul sağlandığı sürece aynı kod bloğunun tekrar tekrar çalıştırılmasını sağlayan yapılardır (`while`).

---

## Örnek Proje: Sayı Tahmin Oyunu

Aşağıdaki kod, bilgisayarın 1 ile 20 arasında rastgele tuttuğu bir sayıyı, kullanıcının yönlendirmelerle (Çok yüksek / Çok düşük) tahmin etmeye çalıştığı basit bir oyundur.

```python
import random  # Rastgele sayılar üretmek için gerekli kütüphane

# 1. Aşama: Başlangıç Değişkenlerini Ayarlama
secret = random.randint(1, 20)  # 1 ile 20 arasında rastgele bir sayı seçer
tries = 0                       # Deneme sayısını tutan değişken
guess = 0                       # Kullanıcının tahminini tutan değişken (1-20 aralığı dışında başlatılır)

print("1 ile 20 arasında bir sayı düşünüyorum...")

# 2. Aşama: Döngü (Kullanıcı doğru bilene kadar tekrarla)
while guess != secret:
    text = input("Bir tahminde bulunun: ")  # Kullanıcıdan girdi al (metin formatında)
    guess = int(text)                       # Metni tamsayıya (integer) çevir
    
    tries = tries + 1                       # Deneme sayısını 1 artır

    # 3. Aşama: Koşullu İfadelerle İpucu Verme
    if guess < 1 or guess > 20:
        print("Sayı aralığın dışında. Tekrar deneyin.")
    elif guess < secret:
        print("Çok düşük, tekrar deneyin.")
    elif guess > secret:
        print("Çok yüksek, tekrar deneyin.")
    else:
        print(tries, "denemede buldunuz!")
```