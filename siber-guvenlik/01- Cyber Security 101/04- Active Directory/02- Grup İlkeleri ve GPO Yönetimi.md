## GPO (Group Policy Object) Mantığı

GPO'lar, OU'lara uygulanan ayarlar ve güvenlik politikaları koleksiyonudur. **Group Policy Management** aracı üzerinden yönetilir.

- **Kapsam (Scope):** Bir GPO bağlandığı OU'ya ve altındaki tüm alt OU'lara (sub-OUs) otomatik olarak uygulanır.
- **İlke Alanları:**
  - **Computer Configuration:** Bilgisayar tabanlı ayarları kapsar.
  - **User Configuration:** Kullanıcı tabanlı ayarları kapsar.

---

## SYSVOL Paylaşımı ve Güncelleme

GPO'lar, Domain Controller üzerinde bulunan **SYSVOL** ağ paylaşımı üzerinden dağıtılır.
- **Varsayılan Dizin:** `C:\Windows\SYSVOL\sysvol\`
- **İlke Eşitleme Komutu:** Yapılan değişikliklerin hemen etkinleşmesi için istemci makinede çalıştırılır:

```powershell
  gpupdate /force
````

## Örnek GPO Uygulamaları

### 1. Denetim Masası Access Kısıtlaması (Restrict Control Panel)

- **Tür:** User Configuration
    
- **Yol:** `User Configuration -> Policies -> Administrative Templates -> Control Panel`
    
- **Ayar:** `Prohibit access to Control Panel and PC settings` -> **Enabled**
    
- **Uygulama:** IT dışındaki departman OU'larına (`Sales`, `Marketing`, `Management`) bağlanır.
    

### 2. Otomatik Ekran Kilitleme (Auto Lock Screen)

- **Tür:** Computer Configuration
    
- **Yol:** `Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Local Policies -> Security Options`
    
- **Ayar:** `Interactive logon: Machine inactivity limit` -> **300 seconds**
    
- **Uygulama:** Kök etki alanına (`thm.local`) bağlanır. Tüm alt cihazlar (`Workstations`, `Servers`, `Domain Controllers`) bu kuralı devralır.