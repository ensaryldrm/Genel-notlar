## 1. Temel Dosya Sistemi ve Gezinme Komutları

Linux dosya sisteminde yönünüzü bulmak ve klasörler arası geçiş yapmak için kullanılan temel komutlar:

* **`pwd` (Print Working Directory):** O an içinde bulunduğunuz klasörün (dizinin) tam yolunu gösterir. (Örn: `/home/ubuntu`)
* **`ls` (List):** Bulunduğunuz dizindeki dosya ve klasörleri listeler.
  * **`ls -l`:** Dosyaları boyut, sahip, izinler ve değiştirilme tarihi gibi ekstra ayrıntılarla listeler.
  * **`ls -al`:** Gizli dosyalar (başında nokta `.` olan dosyalar) dahil olmak üzere tüm dosyaları ayrıntılı listeler.
* **`cd <dizin_adi>` (Change Directory):** Belirtilen klasörün içine girmenizi sağlar. (Örn: `cd Documents`)
  * **`cd ..` :** Bir üst (önceki) klasöre (seviyeye) dönmenizi sağlar.

---

## 2. Dosya Arama ve Okuma

* **`find`:** Dosya sistemi içinde belirli bir dosyayı aramak için kullanılır.
  * *Kullanım örneği:* `find ~ -name gorev.txt` (`~` işareti ana dizini temsil eder; ana dizinde ismi `gorev.txt` olan dosyayı arar ve bulursa tam yolunu ekrana yazdırır).
* **`cat` (Concatenate):** Bir dosyanın içeriğini doğrudan terminal ekranına yazdırmak (okumak) için kullanılır.
  * *Kullanım örneği:* `cat gorev.txt`

---

## 3. Sistem Bilgisi Toplama

Hedef sistemin (veya kendi sisteminizin) durumunu, sürümünü ve donanımını analiz etmek (sağlık kontrolü yapmak) için kullanılan komutlar:

* **`whoami`:** Terminalde o an hangi kullanıcı hesabıyla oturum açtığınızı/işlem yaptığınızı gösterir.
* **`uname`:** İşletim sisteminin temel adını verir (Örn: Linux).
  * **`uname -a`:** Sistem hakkında çekirdek (kernel) sürümü, bilgisayar adı (hostname) ve donanım mimarisi (Örn: x86_64) gibi tüm detaylı bilgileri tek satırda verir.
* **`df -h` (Disk Free):** Sistemdeki disk kullanımını ve boş depolama alanını "insan tarafından okunabilir" (MB, GB cinsinden) formatta gösterir. (`-h` parametresi human-readable anlamına gelir).
* **`/etc` Dizini ve Dağıtım Sürümü:** Linux yapılandırma dosyaları genellikle `/etc` dizininde tutulur. Sistemin tam Linux dağıtımını (Örn: Ubuntu 24.04) ve sürümünü net bir şekilde öğrenmek için ilgili dosya okunur:
  * *Kullanım örneği:* `cat /etc/os-release`