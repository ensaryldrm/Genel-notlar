# Windows Domain ve Active Directory Temelleri

## Windows Domain Nedir?

Windows Domain (Alan Adı), bir işletmenin yönetimi altındaki kullanıcı ve bilgisayarların oluşturduğu gruptur. Ana amaç, ağ üzerindeki ortak bileşenlerin yönetimini **Active Directory (AD)** adı verilen merkezi bir veritabanında toplamaktır.

- **Domain Controller (DC):** Active Directory hizmetlerini çalıştıran sunucudur.
- **Avantajları:**
  - **Merkezi Kimlik Yönetimi:** Tüm kullanıcılar tek noktadan yönetilir.
  - **Güvenlik İlkeleri (GPO):** İlkeler merkezi olarak dağıtılır.

---

## Active Directory Domain Services (AD DS) ve Nesneler

Active Directory, ağdaki tüm varlıkları **nesne (object)** olarak tutar.

### 1. Kullanıcılar (Users)
Kullanıcılar birer **Güvenlik Sorumlusudur (Security Principal)**. Ağa erişecek kişileri veya `IIS`, `MSSQL` gibi servisleri (Service Accounts) temsil edebilir.

### 2. Makineler (Machines)
Ağa katılan her bilgisayar için bir makine hesabı oluşturulur.
- Makineler de birer Güvenlik Sorumlusudur.
- Makine adlarının sonuna **`$`** simgesi gelir (Örn: `DC01$`).
- Parolaları otomatik döndürülür ve genellikle 120 karakterlik rastgele karmaşık dizilerden oluşur.

### 3. Güvenlik Grupları (Security Groups)
Toplu yetkilendirme sağlamak için kullanılır. Gruplar hem kullanıcıları hem de makineleri içerebilir.

| Güvenlik Grubu | Açıklama |
| :--- | :--- |
| **Domain Admins** | Tüm etki alanında tam yetkili yöneticilerdir. |
| **Server Operators** | Domain Controller'ları yönetebilirler. |
| **Backup Operators** | İzinlere bakılmaksızın tüm dosyalara yedekleme amacıyla erişebilirler. |
| **Account Operators** | Hesap oluşturma ve değiştirme yetkisine sahiptirler. |
| **Domain Users** | Etki alanındaki tüm kullanıcıları kapsar. |
| **Domain Computers** | Etki alanındaki tüm bilgisayarları kapsar. |

---

## Organizasyonel Birimler (OUs) ve Konteynerler

- **OU (Organizasyonel Birim):** Kullanıcılara ve bilgisayarlara **ilke (policy)** uygulamak için kullanılan hiyerarşik yapılardır.
- **Kural:** Bir kullanıcı veya bilgisayar aynı anda yalnızca **tek bir OU** içinde yer alabilir.

### Varsayılan Konteynerler
- **Builtin:** Varsayılan sistem grupları.
- **Computers:** Ağa yeni katılan cihazların düştüğü varsayılan klasör.
- **Domain Controllers:** DC sunucularının bulunduğu OU.
- **Users:** Varsayılan kullanıcılar.

### Kazara Silinme Korumasını Kaldırma (Accidental Deletion Protection)
Bir OU silinmek istendiğinde hata alınıyorsa:
1. `ADUC -> View -> Advanced Features` etkinleştirilir.
2. Silinecek OU'ya sağ tıklanıp `Properties -> Object` sekmesine gidilir.
3. `Protect object from accidental deletion` kutusundaki işaret kaldırılır.

---

## Yetki Devri (Delegation) ve Parola Sıfırlama

Admin yetkisi vermeden belirli kullanıcıların (örneğin Helpdesk) belirli OU'lar üzerinde yetkili kılınmasına **Delegation** denir.

### PowerShell ile Parola Sıfırlama (Kısıtlı Yetkili Kullanıcı):

```powershell

# Parolayı sıfırlama
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

# İlk açılışta parola değişimini zorunlu kılma
Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose
