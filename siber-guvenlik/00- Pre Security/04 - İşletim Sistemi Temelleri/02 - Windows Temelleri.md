## 1. Kimlik Doğrulama ve Hesap Türleri

Sisteme erişmeden önce kullanıcıların kimliğini doğrulaması (şifre, PIN vb.) gerekir. Windows'ta izin düzeylerini belirleyen 3 temel hesap türü vardır:

* **Misafir (Guest):** Geçici erişim içindir. Sistem ayarlarını değiştirme yetkisi ve minimum izni vardır.
* **Standart (Standard):** Günlük görevler (uygulama çalıştırma, kişiselleştirme) içindir. Sistem genelinde değişiklik yapamaz.
* **Yönetici (Administrator):** Sistem üzerinde tam kontrole sahiptir. Yazılım yükleyebilir, yapılandırmaları değiştirebilir ve diğer kullanıcıları yönetebilir.

---

## 2. Windows Arayüzü (Masaüstü ve Görev Çubuğu)

Kullanıcı giriş yaptıktan sonra karşılaşılan ilk ana çalışma alanıdır (Havalimanı Terminali analojisi).

* **Masaüstü (Desktop):** Dosyalar, klasörler ve kısayolların barındığı ana alan.
* **Görev Çubuğu (Taskbar):** Ekranın altındaki kontrol şeridi. Şunları içerir:
  * **Başlat Menüsü (Start Menu):** Uygulamalara, ayarlara ve güç seçeneklerine (kapat/yeniden başlat) hızlı erişim (Danışma masası).
  * **Arama (Search):** Dosya ve ayarları anahtar kelimelerle bulma.
  * **Görev Görünümü (Task View):** Açık pencereleri görme ve aralarında geçiş yapma.
  * **Sistem Tepsisi (System Tray):** Ağ, ses, tarih/saat ve bildirimlerin bulunduğu sağ alt köşe.

---

## 3. Dosya ve Sistem Yönetimi

### Dosya Gezgini (File Explorer)
Windows hiyerarşik bir klasör yapısı kullanır (klasörler içinde klasörler).
* **Temel Konumlar:** Masaüstü, Belgeler, İndirilenler.
* **Dosya Yolu (File Path):** Bir dosyanın veya klasörün sistemdeki tam adresidir. (Örn: `C:\Users\Administrator\Desktop\DosyaAdi`)

### Sistem Bilgisi (System Information)
Sistemin donanım ve işletim sistemi detaylarına ulaşmak için **Ayarlar (Settings) > Bilgisayarınız hakkında (About your PC)** menüsü kullanılır.

### Yapılandırma Araçları
* **Windows Ayarları (Windows Settings):** Cihaz, ağ ve güvenlik ayarları için modern, merkezi konum.
* **Denetim Masası (Control Panel):** Belirli gelişmiş yönetimsel görevler için kullanılan eski (legacy) yapılandırma aracı.

---

## 4. Uygulama Yönetimi

Sistem güvenliğini ve performansını sağlamak için uygulamaların yönetimi kritik bir beceridir.

* **Güncelleme (Update):** **Windows Update**, işletim sistemini, yerel uygulamaları ve güvenlik yamalarını güncel tutar.
* **Yükleme (Install):** Uygulamalar **Microsoft Store** üzerinden veya güvenilir kaynaklardan indirilen `.exe` / `.msi` yükleme dosyalarıyla kurulur.
* **Kaldırma (Uninstall):** Ayarlar'daki "Program ekle veya kaldır" veya Denetim Masası'ndaki "Program kaldır" menülerinden yapılır.

---

## 5. Görev Yöneticisi (Task Manager)

Sistemde arka planda ve ön planda çalışan her şeyi gerçek zamanlı izleme aracıdır. 5 ana sekmesi vardır:
1. **Süreçler (Processes):** Çalışan uygulamalar ve ne kadar kaynak tükettikleri.
2. **Performans (Performance):** CPU, RAM ve Ağ kullanımının istatistiksel grafikleri.
3. **Kullanıcılar (Users):** Aktif kullanıcılar ve tükettikleri kaynaklar.
4. **Ayrıntılar (Details):** Çalışan süreçlerin PID (Süreç Kimliği) gibi teknik detayları.
5. **Hizmetler (Services):** Arka plan Windows hizmetlerinin durumu (çalışıyor/durdu).

---

## 6. Windows Güvenliği (Windows Security)

Windows'un varsayılan olarak gelen merkezi güvenlik panosudur.

* **Virüs ve Tehdit Koruması:** Kötü amaçlı yazılımları (malware) bulmak için gerçek zamanlı koruma ve özel tarama (Custom scan) özellikleri.
* **Cihaz Güvenliği & Tarayıcı Denetimi:** Donanım tabanlı koruma ve zararlı sitelere karşı koruma.

### Windows Defender Güvenlik Duvarı (Firewall)
Sisteme gelen (inbound) ve giden (outbound) ağ trafiğini izler, yetkisiz erişimi engeller. 3 farklı ağ profili kullanır:
* **Etki Alanı (Domain):** Şirket ağına bağlıyken.
* **Özel (Private):** Ev veya laboratuvar gibi güvenilir ağlarda.
* **Ortak/Genel (Public):** Kafeler gibi güvenilmeyen açık Wi-Fi ağlarında.