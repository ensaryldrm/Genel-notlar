## 1. Sistem Yapılandırması (`msconfig`)

Temel amacı sistemin açılış (startup) ve önyükleme sorunlarını teşhis etmektir. Çalıştırmak için yerel yönetici yetkisi gereklidir.

### Ana Sekmeler
* **Genel (General):** Sistem açılış modunu seçmeyi sağlar: *Normal*, *Tanılama (Diagnostic)* veya *Seçmeli (Selective)*.
* **Önyükleme (Boot):** İşletim sisteminin önyükleme parametrelerini ve güvenli mod ayarlarını yapılandırır.
* **Hizmetler (Services):** Arka planda çalışan tüm servisleri listeler ve yönetir.
* **Başlangıç (Startup):** Windows istemci sürümlerinde (Win 10/11) başlangıç uygulamalarını yönetmek için **Görev Yöneticisi**'ne yönlendirir. Windows Server sürümlerinde ise kullanıcı düzeyindeki başlangıç ögeleri `Win + R` $\rightarrow$ **`shell:startup`** klasörü üzerinden kontrol edilir.
* **Araçlar (Tools):** Sistem tanılama ve yönetim araçlarına hızlı erişim sağlar.

---

## 2. Gelişmiş Sistem Ayarları ve Performans

Arama çubuğuna `View advanced system settings` yazılarak erişilebilir.

* **Takas Dosyası (Page File / Sanal Bellek):** Physical RAM dolduğunda yavaşlamaları ve çökmeleri önlemek için disk alanını sanal bellek olarak kullanır. 
  * *Erişim:* `Performans > Ayarlar > Gelişmiş > Sanal Bellek`
* **Başlangıç ve Kurtarma (Startup and Recovery):** Mavi Ekran (BSOD) gibi kritik sistem çökmelerinde **Çökme Dökümü (Crash Dump)** dosyası oluşturulmasını sağlar.
  * *Döküm Türleri:* Otomatik, Çekirdek, Küçük (256 KB - Minidump), Tam bellek dökümü veya Yok.

---

## 3. Bilgisayar Yönetimi (`compmgmt.msc`)

Sistemi tek bir arayüzden yönetmeyi sağlayan üç ana bölümden oluşur:

### A. Sistem Araçları (System Tools)
* **Görev Zamanlayıcı (Task Scheduler):** Belirli zamanlarda veya tetikleyicilerle (oturum açma, sistem açılışı vb.) otomatik görev, betik veya uygulama çalıştırır.
* **Olay Görüntüleyici (Event Viewer):** Sistemde meydana gelen olayları ve güvenlik denetim izlerini (`audit trail`) görüntüler.
  * *Olay Türleri:* Hata (Error), Uyarı (Warning), Bilgi (Information), Başarı Denetimi (Success Audit), Başarısızlık Denetimi (Failure Audit).
  * *Standart Günlükler:* Application, Security, Setup, System, Forwarded Events.
* **Paylaşılan Klasörler (Shared Folders):** Ağ üzerindeki paylaşımları (`C$`, `ADMIN$`), aktif oturumları ve açık dosyaları yönetir.
* **Aygıt Yöneticisi (Device Manager):** Bağlı donanımları görüntüler, sürücülerini günceller veya devre dışı bırakır.

### B. Depolama (Storage)
* **Disk Yönetimi (Disk Management):** Yeni disk tanımlama, bölüm genişletme/küçültme ve sürücü harfi atama (`E:`) gibi disk işlemlerini yürütür.

### C. Hizmetler ve Uygulamalar (Services and Applications)
* **Hizmetler (Services):** Arka plan servislerinin durumunu kontrol eder.
  * *Başlangıç Türleri:* Otomatik (Boot ile), Elle (İstek üzerine), Devre Dışı.
* **WMI Denetimi (WMI Control):** Windows Yönetim İletimleri (`WMI`) servisini denetler. (Eski `WMIC` komut satırı aracı deprecated olmuş, yerini PowerShell almıştır).

---

## 4. Sistem Bilgisi (`msinfo32`) ve Kaynak İzleyicisi (`resmon`)

### Sistem Bilgisi (`msinfo32`)
Donanım, sistem bileşenleri ve yazılım ortamı hakkında kapsamlı teknik özet sunar.
* **Donanım Kaynakları:** IRQ, DMA ve bellek adresleri gibi alt seviye detaylar.
* **Bileşenler:** Ekran, girdi cihazları ve ağ bağdaştırıcıları.
* **Yazılım Ortamı:** Yüklü programlar, ağ bağlantıları ve **Çevre Değişkenleri** (`WINDIR` vb.).

### Kaynak İzleyicisi (`resmon`)
Gelişmiş kullanıcılar için gerçek zamanlı performans ve süreç analizi aracıdır.
* **CPU:** Süreçlerin işlemci kullanımı, bağlı DLL ve modüller.
* **Bellek (Memory):** Fiziksel bellek dağılımı ve donanıma ayrılan miktar.
* **Disk:** Okuma/yazma hızları ve disk üzerindeki aktif dosyalar.
* **Ağ (Network):** Ağ trafiği oluşturan süreçler, aktif IP/Port bağlantıları ve dinlenen portlar (`listening ports`).

---

## 5. Komut İstemi (`cmd`) Temelleri

* `hostname`: Bilgisayarın adını gösterir.
* `whoami`: Aktif kullanıcının adını gösterir.
* `ipconfig`: Ağ adresi ayarlarını (IP, Mask, Gateway) gösterir.
* `cls`: Ekranı temizler.
* `/?`: Komutların yardım kılavuzunu açar (Örn: `ipconfig /?`).

### Ağ ve Yönetim Komutları
* `netstat`: Protokol istatistiklerini ve aktif TCP/IP bağlantılarını gösterir (`netstat -a`, `netstat -b`).
* `net`: Ağ kaynaklarını ve kullanıcıları yönetir. Yardım menüsü için `net help [alt-komut]` kullanılır.
  * `net user`: Kullanıcı yönetimi.
  * `net localgroup`: Yerel grup yönetimi.
  * `net share`: Paylaşım yönetimi.

---

## 6. Windows Kayıt Defteri (Registry - `regedit`)

İşletim sistemi, kullanıcı profilleri, yüklü uygulamalar, donanımlar ve port yapılandırmaları için gerekli ayarların saklandığı **merkezi ve hiyerarşik veritabanıdır**. 

* **Düzenleyici:** `regedit`
* **Dikkat:** Yanlış yapılan bir değişiklik sistem kararlılığını bozabilir veya işletim sistemini çökertebilir.