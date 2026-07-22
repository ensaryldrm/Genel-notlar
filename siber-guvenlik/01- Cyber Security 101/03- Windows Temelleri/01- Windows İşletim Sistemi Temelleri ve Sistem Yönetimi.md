## 1. NTFS Dosya Sistemi ve İzinler

Modern Windows sistemlerinde kullanılan varsayılan dosya sistemi **NTFS**'dir (New Technology File System). FAT16/FAT32 gibi eski sistemlerin aksine gelişmiş güvenlik ve performans özelliklerine sahiptir.

### NTFS Özellikleri
* **Günlükleme (Journaling):** Sistem çökmesi durumunda günlük loglarını kullanarak dosyaları otomatik onarabilir.
* **Büyük Dosya Desteği:** 4 GB'tan büyük dosyaları destekler.
* **Sıkıştırma ve Şifreleme:** Dosya seviyesinde sıkıştırma ve EFS (Encrypting File System) şifreleme desteği sunar.
* **Alternatif Veri Akışları (ADS - Alternate Data Streams):** Bir dosyanın varsayılan veri akışı (`$DATA`) dışında gizli veri akışları barındırmasına izin verir. İnternet'ten indirilen dosyaların kaynağını işaretlemek için kullanılır; ancak zararlı yazılımlar veri gizlemek için de kullanabilir.

### NTFS İzin Seviyeleri
Dosya ve klasör erişimlerini denetlemek için kullanılır:
* **Tam denetim (Full control)**
* **Değiştir (Modify)**
* **Okuma ve yürütme (Read & Execute)**
* **Klasör içeriğini listeleme (List folder contents)**
* **Okuma (Read)**
* **Yazma (Write)**

> **Görüntüleme:** Dosya/Klasör Sağ Tık $\rightarrow$ Özellikler (Properties) $\rightarrow$ Güvenlik (Security) sekmesi.

---

## 2. Kritik Windows Dizinleri ve Çevre Değişkenleri

* **`%windir%` (`C:\Windows`):** İşletim sisteminin kurulu olduğu ana klasördür.
* **`C:\Windows\System32`:** İşletim sisteminin çalışması için kritik öneme sahip tüm sistem dosyalarını ve yönetim araçlarını barındırır. Bu klasörden dosya silinmesi sistemi çalışamaz hale getirebilir.
* **`C:\Users`:** Sistemdeki tüm kullanıcı profillerinin bulunduğu ana dizindir. İlk oturum açılışında `User Profile Service` tarafından oluşturulur.
  * Her kullanıcı dizini altında *Masaüstü (Desktop)*, *Belgeler (Documents)*, *İndirilenler (Downloads)* gibi standart klasörler yer alır.

---

## 3. Kullanıcı Yönetimi ve UAC (Kullanıcı Hesabı Denetimi)

### Kullanıcı Türleri
* **Yönetici (Administrator):** Sistem düzeyinde değişiklik yapabilir, program yükleyebilir, kullanıcı/grup yönetimi yapabilir.
* **Standart Kullanıcı (Standard User):** Yalnızca kendisine ayrılan alanlarda değişiklik yapabilir; sistem ayarlarını değiştiremez ve program yükleyemez.

### Kullanıcı Yönetim Araçları
* **Ayarlar:** `Sistem Ayarları > Diğer kullanıcılar`
* **Yerel Kullanıcılar ve Gruplar:** `Çalıştır (Win + R)` $\rightarrow$ **`lusrmgr.msc`**
  * Kullanıcılar gruplara atanır ve atandıkları grubun izinlerini devralırlar.

### Kullanıcı Hesabı Denetimi (UAC - User Account Control)
* Standart kullanıcıların veya yükseltilmemiş oturumların sisteme izinsiz müdahale etmesini önler.
* Yüksek ayrıcalık gerektiren bir işlem çalıştırıldığında kullanıcıdan onay veya yönetici şifresi ister.
* Yönetici yetkisi gerektiren programların simgelerinde **kalkan (shield)** simgesi bulunur.

---

## 4. Sistem Ayarları ve Denetim Masası

* **Ayarlar (Settings):** Windows 8/10/11 ile gelen, kullanıcı dostu birincil ayar menüsüdür.
* **Denetim Masası (Control Panel):** Gelişmiş ve karmaşık sistem ayarlarının yapıldığı klasik menüdür.
* **Programlar ve Özellikler:** `Denetim Masası > Programlar > Programlar ve Özellikler` yolu izlenerek sistemde yüklü tüm uygulamalar, yayıncıları ve sürümleri görüntülenebilir/kaldırılabilir.

---

## 5. Görev Yöneticisi (Task Manager)

* Sistemde o anda çalışan tüm uygulama ve süreçleri (processes) listeler.
* **Performans (Performance)** sekmesinde anlık CPU, RAM, Disk ve Ağ kullanım oranlarını izleme imkanı sunar.
* **Erişim:** Görev çubuğuna sağ tık $\rightarrow$ *Görev Yöneticisi* (Tüm ayrıntıları görmek için *Diğer ayrıntılar / More details* seçeneğine tıklanır).