## 1. Yetki ve Kullanıcı Kavramları

Sistem üzerinde tam kontrole sahip en üst düzey hesaplar:
* **root:** Linux, Android ve Apple sistemlerinde en yüksek yetkiye sahip hesaptır.
* **administrator:** MS Windows sistemlerinde en yüksek yetkiye sahip hesaptır.
* Bu hesaplar sistem üzerinde tam ve sınırsız erişime sahiptir.

---

## 2. SSH (Secure Shell) ile Uzak Erişim

Uzak bir Linux sistemine güvenli bir şekilde bağlanmak için SSH kullanılır.

* **Komut:** `ssh KULLANICI_ADI@MAKİNE_IP`
* **Not:** SSH üzerinden şifre girerken terminalde herhangi bir karakter (yıldız, nokta vb.) görünmez; ancak sistem girişi alır.
* **İlk Bağlantı:** Bir sunucuya ilk kez bağlanıldığında, sistem sunucunun parmak izini (fingerprint) doğrulamak için `yes/no` onayı ister. `yes` ile devam edilir.

---

## 3. Temel Linux Komutları (Özet)

Sisteme sızdıktan sonra ortamı tanımak için kullanılan temel komutlar:

* **`whoami`:** Mevcut oturumdaki kullanıcı adını doğrular.
* **`ls` (List):** Mevcut dizindeki (gizli olmayan) tüm dosya ve klasörleri listeler.
* **`cat <DOSYA_ADI>`:** Bir dosyanın metin içeriğini terminal ekranına yazdırır.
* **`history`:** O kullanıcı tarafından daha önce çalıştırılmış olan komut geçmişini listeler (Güvenlik analizi için çok değerlidir).

---

## 4. Yetki Yükseltme ve Hesap Geçişleri

* **`su - <KULLANICI_ADI>` (Substitute User):** Mevcut oturumda, başka bir kullanıcı hesabına geçiş yapmak için kullanılır.
* **Saldırı Senaryosu:** Eğer sistemde başka kullanıcılar (johnny, linda vb.) olduğu biliniyorsa, bu kullanıcıların şifrelerini kırmak veya tahmin etmek için `ssh` (sistem dışındayken) veya `su` (sistem içindeyken) komutları kullanılarak manuel "brute-force" denemeleri yapılabilir.

---

## Güvenlik İpucu
* **Parola Yeniden Kullanımı:** Farklı platformlarda aynı şifreyi kullanmak, bir servisin hacklenmesi durumunda tüm diğer hesaplarınızın da tehlikeye girmesine neden olur.