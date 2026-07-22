## 1. Temel Programlama Kavramları

* **`let` (Değişkenler):** Değeri programın ilerleyen kısımlarında değiştirilebilecek verileri saklamak için kullanılır (Örn: Deneme sayısı, kullanıcının tahmini).
* **`const` (Sabitler):** Program boyunca değeri asla değişmeyecek verileri tanımlamak için kullanılır (Örn: Hedef gizli sayı).
* **Koşullu İfadeler (`if`, `else if`, `else`):** Verilen kararlara göre (tahminin yüksek, düşük veya doğru olması) farklı sonuçlar üretir.
* **Döngüler (`while`):** Belirli bir şart sağlandığı sürece kodun tekrar tekrar çalışmasını sağlar (Kullanıcı doğru tahminde bulunmadığı sürece yeni tahmin istemek).

---

## 2. Kullanışlı Fonksiyonlar ve Metotlar

* **`console.log()`:** Ekrana çıktı (metin) yazdırmak için kullanılır.
* **`Math.random()`:** 0 ile 1 arasında rastgele ondalıklı bir sayı üretir.
* **`Math.floor()`:** Ondalıklı bir sayıyı en yakın alt tamsayıya yuvarlar.
* **`parseInt(text, 10)`:** Metin formatındaki bir sayıyı, 10 tabanında bir tamsayıya (integer) dönüştürür.

---

## 3. Örnek Proje: Sayı Tahmin Oyunu

Aşağıdaki kod, Node.js kullanılarak komut satırında çalışan, kullanıcının bilgisayarın tuttuğu sayıyı bulmaya çalıştığı oyunun tamamlanmış halidir.

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
    // 1. Aşama: Başlangıç Ayarları
    // 1 ile 20 arasında rastgele bir sabit sayı üretir
    const secret = Math.floor(Math.random() * 20) + 1; 
    let tries = 0;
    let guess = 0; // Şartı başlatmak için imkansız bir sayı atanır

    console.log("1 ile 20 arasında bir sayı düşünüyorum...");

    // 2. Aşama: Döngü (Kullanıcının tahmini, gizli sayıya eşit "olmadığı sürece" çalışır)
    while (guess !== secret) {
        // Kullanıcıdan metin formatında girdi alınır
        const text = await rl.question("Bir tahminde bulunun: "); 
        guess = parseInt(text, 10); // Girdi tamsayıya çevrilir

        tries = tries + 1; // Deneme sayacı artırılır

        // 3. Aşama: Karşılaştırma ve Geri Bildirim
        if (guess < 1 || guess > 20) {
            console.log("Sayı aralığın dışında. Tekrar deneyin.");
        } else if (guess < secret) {
            console.log("Çok düşük, tekrar deneyin.");
        } else if (guess > secret) {
            console.log("Çok yüksek, tekrar deneyin.");
        } else {
            console.log(tries, "denemede buldunuz!");
        }
    }
} finally {
    // İşlem bittiğinde veri girişini sonlandır
    rl.close();
}