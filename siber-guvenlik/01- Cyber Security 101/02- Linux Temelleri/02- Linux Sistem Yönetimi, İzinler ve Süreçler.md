## 1. Dosya İzinleri ve Kullanıcılar

### Kullanıcılar Arasında Geçiş (`su`)
* **`su kullaniciadi`**: Belirtilen kullanıcıya geçiş yapar ancak önceki kullanıcının çalışma dizininde bırakır.
* **`su -l kullaniciadi`** (veya `--login`): Yeni kullanıcının ortam değişkenlerini ve kendi ev dizinini (`/home/...`) tamamen devralarak geçiş yapar.

### Sayısal İzin Formatı (Numeric Permissions)
Linux'ta izinler 3 ana gruba ayrılır: **Sahip (Owner)**, **Grup (Group)**, **Diğerleri (Others)**.
* **İzin Değerleri:** Okuma (`r` = 4), Yazma (`w` = 2), Çalıştırma (`x` = 1)
* **Örnek Hesaplama (`rwxrwxrwx`):** 4+2+1 = 7 (Her grup için ayrı ayrı toplanır, örn: `777`).

**Yaygın İzin Örnekleri:**
* **`755` (`rwxr-xr-x`):** Sahip her şeyi yapabilir, diğerleri yalnızca okuyabilir ve çalıştırabilir.
* **`644` (`rw-r--r--`):** Sahip okuyabilir/yazabilir, diğerleri yalnızca okuyabilir.
* **`700` (`rwx------`):** Yalnızca dosya sahibi erişebilir.
* *Örnek Komut:* `chmod 750 system_overview.txt` (Sahip: Tam, Grup: Okuma+Çalıştırma, Diğerleri: Yok).

---

## 2. Önemli Kök (Root) Dizinler

* **`/etc`**: Sistem dosyalarının saklandığı yerdir (Örn: `sudoers`, şifrelerin tutulduğu şifrelenmiş `passwd` ve `shadow` dosyaları).
* **`/var`**: Sıkça erişilen veya yazılan verileri/servis loglarını tutar (`/var/log`).
* **`/root`**: Sistem yöneticisinin (`root`) kendi ev (home) dizinidir.
* **`/tmp`**: Geçici (temporary) verilerin tutulduğu yerdir. Bilgisayar yeniden başlatıldığında temizlenir. **Varsayılan olarak her kullanıcı bu klasöre yazabilir**, bu yüzden pentest'lerde betik yüklemek için sıkça kullanılır.

---

## 3. Uzaktan Dosya Aktarımı ve Sunma

### `wget` (Web'den Dosya İndirme)
* Web üzerinden HTTP ile dosya indirir: 
  `wget https://ornek.com/dosya.txt`

### `scp` (SSH Üzerinden Güvenli Kopyalama)
* **Yerelden Uzağa:** `scp dosya.txt kullanici@IP_Adresi:/hedef/yol/dosya.txt`
* **Uzak Yerden Yere:** `scp kullanici@IP_Adresi:/uzak/yol/dosya.txt yerel_dosya.txt`

### Python ile HTTP Sunucusu Başlatma
* Bulunulan dizindeki dosyaları web üzerinden sunmak için:
  `python3 -m http.server 8000`
* Başka bir makineden indirmek için:
  `wget http://IP_Adresi:8000/dosya_adi`

---

## 4. Süreç (Process) Yönetimi

* **`ps`**: O anki oturumdaki süreçleri listeler.
* **`ps aux`**: Sistemdeki tüm kullanıcıların ve arka plan servislerinin süreçlerini gösterir.
* **`top`**: Çalışan süreçleri eş zamanlı (real-time) olarak izler.
* **`kill [PID]`**: Belirtilen süreci sonlandırır.
  * `SIGTERM`: Süreci temizlik yaparak sonlandırır.
  * `SIGKILL`: Süreci zorla/ani şekilde sonlandırır.
  * `SIGSTOP`: Süreci askıya alır.

### Systemd ve Servis Yönetimi (`systemctl`)
* **`systemctl start [servis]`**: Servisi başlatır.
* **`systemctl stop [servis]`**: Servisi durdurur.
* **`systemctl enable [servis]`**: Sistem açılışında (boot) otomatik başlamasını sağlar.
* **`systemctl disable [servis]`**: Açılıştan kaldırır.
* **`systemctl status [servis]`**: Durumunu gösterir.

### Arka Plan ve Ön Plan İşlemleri
* Komut sonuna **`&`** eklemek: Sürecin arka planda çalışmasını sağlar.
* **`Ctrl + Z`**: Çalışan ön plan sürecini askıya alır ve arka plana atar.
* **`fg`**: Arka plandaki süreci tekrar ön plana getirir.

---

## 5. Zamanlanmış Görevler (`Crontab`)

Sistem açıldıktan sonra veya belirli periyotlarda otomatik çalıştırılacak görevleri yönetir.
* **Düzenleme Komutu:** `crontab -e`
* **Zaman Formatı (6 Alan):** `MIN HOUR DOM MON DOW CMD`
  * `MIN`: Dakika (0-59)
  * `HOUR`: Saat (0-23)
  * `DOM`: Ayın günü (1-31)
  * `MON`: Ay (1-12)
  * `DOW`: Haftanın günü (0-6)
  * `CMD`: Çalıştırılacak komut
* *Örnek (Her 12 saatte bir yedekleme):* `0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/`

---

## 6. Paket Yönetimi (`apt` ve Depolar)

* **`apt`**: Paket yönetim aracıdır (`dpkg` altyapısını kullanır).
* **GPG Anahtarları:** Ekstra depolardan indirilen yazılımların güvenilirliğini doğrulamak için güvenlik kontrolü sağlar.
* **Depo Ekleme Adımları:**
  1. GPG anahtarını ekle: `wget -qO - url | sudo apt-key add -`
  2. `/etc/apt/sources.list.d/` altında `.list` dosyası oluşturup depo adresini kaydet.
  3. Listeyi güncelle: `sudo apt update`
  4. Kurulum yap: `sudo apt install [yazilim-adi]`
* **Kaldırma:** `sudo apt remove [yazilim-adi]`

---

## 7. Log Dosyaları

Sistemde çalışan uygulamaların ve servislerin kayıt tuttuğu yerdir (`/var/log`).
* **Önemli Loglar:**
  * **Apache2 / Web Sunucuları:** `access.log` (Gelen istekler), `error.log` (Hatalar).
  * **Fail2ban:** Kaba kuvvet saldırı girişimlerini izler.
  * **UFW:** Güvenlik duvarı kayıtları.
* **Log Döndürme (Rotating):** İşletim sistemi, logların şişmesini önlemek için bunları otomatik olarak yönetir ve arşivler.