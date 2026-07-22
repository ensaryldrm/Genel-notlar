## 1. Windows Güvenliği Genel Bakış

Windows Güvenliği (Windows Security), cihazı ve verileri koruyan araçların yönetildiği merkezi arayüzdür. `Ayarlar > Güncelleştirme ve Güvenlik > Windows Güvenliği` üzerinden erişilir.

### Durum Simgeleri
* **Yeşil:** Cihaz yeterince korunuyor, yapılması gereken eylem yok.
* **Sarı:** Gözden geçirilmesi gereken güvenlik önerisi var.
* **Kırmızı:** Acil müdahale gerektiren bir güvenlik riski/uyarısı var.

---

## 2. Virüs ve Tehdit Koruması (Virus & Threat Protection)

### Tarama Seçenekleri
* **Hızlı Tarama (Quick Scan):** Yaygın tehdit konumlarını denetler.
* **Tam Tarama (Full Scan):** Diskteki tüm dosya ve çalışan süreçleri taranır.
* **Özel Tarama (Custom Scan):** Kullanıcının seçtiği dosya/klasörleri denetler.

### Tehdit Yönetimi
* **Karantinaya Alınan Tehditler (Quarantined Threats):** Çalışması engellenip izole edilmiş ve periyodik olarak silinen zararlılar.
* **İzin Verilen Tehditler (Allowed Threats):** Kullanıcının tehdit uyarısına rağmen çalışmasına manuel onay verdiği ögeler.

### Kritik Koruma Ayarları
* **Gerçek Zamanlı Koruma (Real-time Protection):** Kötü amaçlı yazılımların çalışmasını/yüklenmesini anlık engeller.
* **Bulut Tabanlı Koruma:** Güncel tehdit imzalarına erişim için bulut veritabanını kullanır.
* **Denetimli Klasör Erişimi (Controlled Folder Access):** Yalnızca güvenilir uygulamaların korunan klasörlerde değişiklik yapmasına izin vererek fidye yazılımlarına (Ransomware) karşı koruma sağlar.
* **Dışlananlar (Exclusions):** Antivirüsün taramasını istemediğimiz dosya/klasör listesi. Yanlış pozitifleri (False Positive) önlemek için kullanılır; ancak yanlış kullanımı güvenlik zafiyeti yaratır.

> **İpucu:** Sağ tık menüsünden `Microsoft Defender ile tara` seçeneğiyle isteğe bağlı (on-demand) tarama yapılabilir.

---

## 3. Güvenlik Duvarı ve Ağ Koruması (Firewall & Network Protection)

Güvenlik duvarı, ağ portlarından giren ve çıkan trafiği denetleyen güvenlik katmanıdır.

### Ağ Profilleri
1. **Alan Adı (Domain):** Bir Domain Controller'a (Active Directory) bağlı şirket/kurum ağları.
2. **Özel (Private):** Güvenilir ev veya yerel ağlar.
3. **Ortak (Public):** Otel, kafe veya halka açık Wi-Fi ağları gibi varsayılan ve en kısıtlayıcı profil.

> **Hızlı Erişim Komutu:** **`WF.msc`** (Windows Defender Firewall with Advanced Security)

---

## 4. Uygulama ve Tarayıcı Denetimi (App & Browser Control)

* **Microsoft Defender SmartScreen:** Kimlik avı (Phishing) sitelerine, zararlı web içeriklerine ve tanınmayan internet indirmelerine karşı koruma sağlar. (*Uyar / Engelle / Kapat* modları vardır).
* **Exploit Protection:** İşletim sistemine entegre, bellek ve sistem açıklarını istismar eden saldırılara karşı koruma sağlayan katmandır.

---

## 5. Donanım Tabanlı Güvenlik: TPM ve BitLocker

### Çekirdek Yalıtımı (Core Isolation)
* **Bellek Bütünlüğü (Memory Integrity):** Sanallaştırma tabanlı güvenlik (VBS) kullanarak zararlı kodların yüksek güvenlikli sistem süreçlerine sızmasını engeller.

### TPM (Trusted Platform Module)
* Şifreleme işlemlerini yürütmek üzere tasarlanmış donanım tabanlı güvenli bir kripto işlemcidir.
* Fiziksel müdahalelere ve zararlı yazılımların güvenlik işlevlerini kurcalamasına karşı dayanıklıdır.

### BitLocker Sürücü Şifrelemesi
* Diskteki verileri şifreleyerek çalınma, kaybolma veya yetkisiz fiziksel erişim durumlarında veri sızıntısını önler.
* En yüksek güvenliği **TPM 1.2+** çipi ile birlikte çalışarak sunar (sistem çevrimdışıyken kurcalanmadığını doğrular).

---

## 6. Cilt Gölge Kopyası Hizmeti (Volume Shadow Copy Service - VSS)

VSS, yedeklenecek verilerin tutarlı bir anlık görüntüsünü (snapshot / point-in-time copy) oluşturur.

* **Depolama Alanı:** Her korunan sürücüdeki `System Volume Information` gizli klasörüdür.
* **İşlevleri:** Sistem geri yükleme noktası oluşturma, geri yükleme yapma ve yönetme.

### Siber Güvenlik ve Tehdit Perspektifi
Fidye yazılımları (Ransomware), kurbanın fidye ödemeden sistemini geri yüklemesini engellemek için ilk olarak VSS gölge kopyalarını silmeyi hedefler (`vssadmin delete shadows`). Çevrimdışı (offline/off-site) yedek bulunmuyorsa verileri kurtarmak imkansız hale gelebilir.