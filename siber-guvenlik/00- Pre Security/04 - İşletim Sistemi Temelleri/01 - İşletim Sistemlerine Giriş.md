## 1. İşletim Sisteminin Temel Görevleri

Merkezi bir organizatör olan işletim sistemi olmasaydı, her program donanıma doğrudan müdahale etmeye çalışır ve sistem çökerdi. Temel görevleri şunlardır:

* **Süreç Yönetimi (Process Management):** Çalışan programları başlatır, işlemci (CPU) zamanını paylaştırır (Multitasking/Çoklu görev).
* **Bellek Yönetimi (Memory Management):** Her programa yetecek kadar RAM ayırır, birbirlerinin belleğine müdahale etmelerini engeller. RAM dolduğunda sanal bellek kullanır.
* **Dosya Yönetimi (File Management):** Dosyaları klasörler halinde düzenler, izinleri (okuma/yazma) ve meta verileri (boyut, oluşturma tarihi) yönetir.
* **Kullanıcı Yönetimi (User Management):** Kullanıcı hesaplarını ayırır ve kimlik doğrulama ile herkesin sadece kendi dosyalarına erişmesini sağlar.
* **Cihaz Yönetimi (Device Management):** Sürücüler (Drivers) aracılığıyla donanımlar (yazıcı, fare vb.) ile uygulamalar arasında evrensel bir iletişim dili kurar.
* **Güvenlik (Security):** Kimlik doğrulama, izin yönetimi, dosya yalıtımı (izolasyon) ve kritik sistem korumasını antivirüslerden önce bizzat OS yapar.

---

## 2. Sistem Ayrıcalık Katmanları (Privilege Layers)

İşletim sistemleri, güvenlik ve kararlılık için yetkileri katmanlara böler:

* **Çekirdek Alanı (Kernel Space):** İşletim sisteminin kalbi olan **Kernel'in** çalıştığı alandır. Donanıma (CPU, RAM, Disk) doğrudan ve tam erişimi vardır (Hava Trafik Kontrol Kulesi).
* **Kullanıcı Alanı (User Space):** Günlük kullandığımız uygulamaların (tarayıcı, oyunlar) çalıştığı, yetkileri kısıtlanmış alandır. Donanıma erişmek için çekirdekten izin (System Call) istemek zorundadırlar (Yolcular ve uçaklar).

---

## 3. Kullanıcı Arayüzleri (Interfaces)

İşletim sistemiyle iki ana yolla etkileşime gireriz:

* **GUI (Grafik Kullanıcı Arayüzü):** Klasörler, simgeler ve pencerelerden oluşur. Tıklayarak işlemler yapılır (Örn: Masaüstü).
* **CLI (Komut Satırı Arayüzü):** İşletim sistemine doğrudan yazılı komutlar (metin) verilerek işlem yapılan siyah ekrandır (Örn: CMD, Terminal). Doğru komutlar bilindiğinde çok daha hızlı ve hassastır.

---

## 4. İşletim Sistemi Türleri ve Aileleri

Her cihazın ihtiyacı farklı olduğu için tek bir "en iyi" işletim sistemi yoktur. İhtiyaca göre çeşitlenmişlerdir:

### Kullanım Amaçlarına Göre
* **Masaüstü (Desktop):** Son kullanıcı odaklı, görsel arayüzü zengin (Windows, macOS, Linux/Ubuntu).
* **Sunucu (Server):** 7/24 kesintisiz çalışma, yüksek performans ve güvenlik odaklı. Genellikle arayüzü yoktur (Linux Server, Windows Server).
* **Mobil (Mobile):** Dokunmatik ekran ve düşük güç tüketimi odaklı (Android, iOS).
* **Gömülü (Embedded):** Sadece belirli bir işi yapmak üzere beyaz eşya, araç veya yönlendiricilere (router) yüklenen hafif sistemler.
* **Sanal/Bulut:** Konteynerler ve sanal makineler için optimize edilmiş çok hafif sistemler (Alpine Linux).