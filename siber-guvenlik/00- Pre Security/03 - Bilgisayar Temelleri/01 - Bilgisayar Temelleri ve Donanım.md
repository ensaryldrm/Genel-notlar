## 1. Temel Bilgisayar Bileşenleri (İnsan Vücudu Analojisi)

Bilgisayar parçalarının görevlerini anlamak için insan vücudu ile basit bir analoji kurabiliriz:

* **Anakart (İskelet ve Sinir Sistemi):** Tüm farklı bileşenleri yerinde tutar ve onları birbirine bağlar. CPU, RAM ve diğer kartlar üzerindeki yuvalara veya portlara takılır.
* **CPU / İşlemci (Beyin):** Beynimizin komutları yerine getirmesi gibi, bilgisayardaki tüm işlemleri ve komutları yürütür. Modern işlemciler paralel işlem yapabilen çoklu çekirdeklere sahiptir.
* **RAM / Rastgele Erişimli Bellek (Kısa Süreli Hafıza):** İşlemcinin hızlıca erişmesi gereken aktif verileri geçici olarak tutar. Elektrik kesildiğinde içindeki veriler kaybolur (uçucudur). 
* **HDD ve SSD / Depolama (Uzun Süreli Hafıza):** Verilerin kalıcı olarak kaydedildiği yerdir. HDD'ler hareketli parçalara sahip daha eski ve yavaş bir teknoloji iken, SSD'ler bellek yongaları kullanarak çok daha yüksek hızlar sunar.
* **Ağ Bağdaştırıcısı (İletişim / Ses Telleri):** Bilgisayarların ağ üzerinden diğer sistemlerle iletişim kurmasını sağlar (Kablolu veya Kablosuz / Wi-Fi).
* **PSU / Güç Kaynağı Ünitesi (Kalp ve Akciğerler):** Tıpkı kalbin kan pompalaması gibi, elektrik prizinden aldığı gücü tüm sistem bileşenlerine dağıtır. 
* **GPU / Ekran Kartı (Görme Merkezi):** İşletim sistemi ve programlardan aldığı bilgileri işleyerek monitöre görsel veri (görüntü) olarak aktarır.
* **Giriş ve Çıkış Aygıtları - I/O (Duyular ve Tepkiler):** Bilgi toplamak için *Giriş* (Klavye, fare, mikrofon) ve işlenen bilgiyi sunmak için *Çıkış* (Monitör, hoparlör, yazıcı) aygıtları kullanılır.

---

## 2. Bilgisayarın Başlatılma (Boot) Süreci

Sistemin düğmesine basıldığında, karşımıza işletim sistemi arayüzü gelene kadar arka planda şu 5 temel adım gerçekleşir:

1. **Güç Düğmesine Basmak:** Gücün donanımlara akması için PSU'ya sinyal gönderilir (Vücudun uyanıp kan pompalamaya başlaması).
2. **Bellenimin (Firmware) Başlaması:** Bileşenlerin uyanmasını sağlayan sistem devreye girer. Bu merkezi yönetici sisteme **UEFI** (Unified Extensible Firmware Interface) veya eski adıyla **BIOS** denir.
3. **POST (Açılışta Kendi Kendini Sınama):** UEFI devreye girdikten sonra donanımların doğru çalışıp çalışmadığını, eksik parça olup olmadığını test eder. (Power-On Self Test).
4. **Önyükleme (Boot) Aygıtını Seçmek:** Sistem sorunsuzsa, UEFI önceden belirlenmiş listeye bakarak işletim sisteminin hangi diskte (HDD/SSD/USB) olduğunu arar.
5. **Önyükleyiciyi (Bootloader) Başlatmak:** İşletim sistemini barındıran disk bulunduğunda, "bootloader" devreye girer. İşletim sistemini diskten alıp **RAM'e** yükler. Ardından donanımların kontrolü UEFI'den İşletim Sistemine geçer.