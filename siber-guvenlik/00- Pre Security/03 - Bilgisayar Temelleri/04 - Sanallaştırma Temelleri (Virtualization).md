## 1. Sanallaştırma Öncesi Dönem ve Sorunlar

Sanallaştırmadan önce genel BT kuralı **"Bir sunucu = bir uygulama"** şeklindeydi. Her hizmet (web sitesi, veritabanı, e-posta) için ayrı bir fiziksel sunucu gerekiyordu.

Bu yaklaşımın yarattığı temel sorunlar şunlardı:
* **Yüksek Maliyet:** Donanım, elektrik, soğutma ve veri merkezi alanı masrafları.
* **Düşük Kullanım Oranı (Verimsizlik):** Sunucular genellikle %5-20 kapasiteyle çalışarak CPU, RAM ve disk kaynaklarını israf ediyordu.
* **Yavaş Devreye Alma:** Yeni fiziksel sunucuların kurulması günler/haftalar sürüyordu.
* **Ölçeklendirme Zorluğu:** Kaynak ihtiyacı arttığında yeni bir donanım satın almak zorunluydu.

---

## 2. Sanallaştırma Nedir? (Bina Analojisi)

Sanallaştırma, birden fazla uygulamanın aynı fiziksel sunucuyu güvenli bir şekilde paylaşmasını sağlar. Bunu bir bina analojisi ile açıklayabiliriz:

* **Fiziksel Sunucu = Bina:** Temel altyapı (Elektrik, su, asansör).
* **Sanal Makine (VM) = Daireler:** Kendi kapısı ve mahremiyeti olan bağımsız yaşam alanları.
* **Uygulamalar / İşletim Sistemleri = Kiracılar:** Dairede yaşayanlar.
* **Hipervizör = Bina Yöneticisi:** Binayı güvenle bölen ve kaynakları dağıtan sistem.

---

## 3. Hipervizör (Hypervisor)

Fiziksel bir bilgisayarı birden fazla sanal bilgisayara (Sanal Makine / VM) bölen ve yöneten temel yazılımdır. CPU, bellek ve depolama paylarını dağıtır, sistemleri izole eder ve yaşam döngülerini yönetir.

| Özellik | Tip 1 Hipervizör (Donanım Seviyesi) | Tip 2 Hipervizör (İşletim Sistemi Seviyesi) |
| :--- | :--- | :--- |
| **Çalışma Şekli** | Doğrudan fiziksel donanım üzerinde çalışır. | Mevcut bir işletim sistemi (Windows/macOS) üzerinde çalışır. |
| **Avantajları** | Çok hızlı, verimli ve güvenlidir. | Kurulumu ve kullanımı kolaydır. |
| **Kullanım Alanı** | Canlı (Production) sunucular, Veritabanları, Veri Merkezleri. | Yazılım/Zararlı dosya testi, Öğrenme (Ev laboratuvarları), Kali Linux. |
| **Örnekler** | VMware ESXi, Microsoft Hyper-V | Oracle VirtualBox, VMware Workstation |

---

## 4. Sanal Makineler ve Konteynerler

Uygulamaları çalıştırmak için kullanılan iki temel sanallaştırma yöntemi vardır:

### Sanal Makineler (VM - Virtual Machine)
* Gerçek bilgisayarın içinde yer alan, kendi işletim sistemine sahip **tam bir sanal bilgisayardır**. (Bina analojisindeki "Daire")
* Kendi sanal işlemcisine (CPU), RAM'ine, diskine ve ağına sahiptir.
* Diğer VM'lerden tamamen izole edilmiştir. Biri çökerse diğeri etkilenmez.
* Maksimum esneklik ve izolasyon sağlar ancak boyutları büyüktür ve daha fazla kaynak tüketir.

### Konteynerler (Containers)
* Tek bir uygulamayı çalıştıran **hafif ve izole edilmiş** bir ortamdır. (Bina analojisindeki "Dairenin içindeki Odalar")
* Yeni bir işletim sistemi kurmak yerine, ana makinenin (host) işletim sistemi **çekirdeğini (kernel) paylaşırlar**.
* Neredeyse anında başlatılırlar ve VM'lere göre çok daha az kaynak tüketirler.
* İçinde çalışacağı sistemle (Örn: Linux ana makinede Linux konteyneri) uyumlu olmalıdır.
* **Docker:** Konteynerleri dağıtmanın ve yönetmenin en yaygın platformudur.

---

## 5. Sanallaştırmanın Temel Avantajları

* **Maliyet Tasarrufu:** Daha az fiziksel cihaz ile daha çok iş.
* **Verimli Kaynak Kullanımı:** Atıl donanım kapasitesinin değerlendirilmesi.
* **Güvenli Test Ortamı:** Zararlı yazılımların ana sistemi etkilemeden izole bir şekilde test edilebilmesi.
* **Hızlı Devreye Alma (Deployment):** Saniyeler/dakikalar içinde yeni bir sistemin ayağa kaldırılabilmesi.
* **Merkezi Yönetim ve Taşınabilirlik:** Sistemlerin kolayca yedeklenip, başka donanımlara taşınabilmesi.