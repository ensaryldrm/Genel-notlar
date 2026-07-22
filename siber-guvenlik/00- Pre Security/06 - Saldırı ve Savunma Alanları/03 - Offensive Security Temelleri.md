## 1. Temel Terminoloji

* **Kapsam (Scope):** Bir güvenlik testi sırasında izin verilen kesin sistemler ve eylemlerdir (Nelerin test edileceği ve nelerin sınır dışı olduğu).
* **Güvenlik Açığı / Zafiyet (Vulnerability):** Bir sistemde, uygulamada veya yapılandırmada saldırganın içeri girmek için kullanabileceği gizli zayıflık veya kusurdur.
* **İstismar (Exploit):** Belirli bir sonuca ulaşmak (veri çalmak, erişim sağlamak vb.) amacıyla bir güvenlik açığından yararlanmak için kullanılan yöntem veya tekniktir.
* **Numaralandırma / Bilgi Toplama (Enumeration):** Zayıf noktaları bulmak için bir sistem, kullanıcılar ve hizmetler hakkında ayrıntılar toplamaktır.
* **Kırmızı Takım (Red Teaming):** Savunmaların etkinliğini test etmek için gerçek bir düşmanı (adversary) simüle eden yapılandırılmış, izinli saldırı metodolojisidir.
* **Sızma Testi (Penetration Test):** Gerçek dünyadaki riskleri anlamak için yetkili bir testçinin güvenlik açıklarını belirleyip sömürmeye çalıştığı değerlendirmedir.
* **Kimlik Doğrulama (Authentication):** Birisinin iddia ettiği kişi olup olmadığını kontrol eden adımdır.
* **Kimlik Bilgileri (Credentials):** Erişimin kilidini açan kullanıcı adları ve şifrelerdir.

---

## 2. Bir Hacker Gibi Düşünmek (Mindset)

Etik hackerlar riskleri gerçek saldırganlardan önce bulur ve kanıtlarlar.

* **Soru sorun:** Bir özelliğin sadece tasarlandığı gibi çalıştığını varsaymayın ("Nasıl kötüye kullanılabilir?", "Ya çalışmazsa?").
* **Beklenmeyeni test edin:** Geliştiricilerin hiç düşünmediği eylemleri ve girdileri (inputs) deneyin.
* **Küçük zayıflıkları zincirleyin (Chain weaknesses):** Tek bir zayıflık (örn. gizli bir giriş sayfası), başka bir zayıflıkla (örn. zayıf şifreler) birleştiğinde bir domino etkisi yaratıp sistemin çökmesine neden olabilir.
* **Düşman gibi düşünün:** "Kötü niyetli bir aktör bu hedefe nasıl yaklaşırdı?"

### Hedefteki Değerli Veriler
Saldırganlar sisteme girdiklerinde genellikle şunları hedefler:
1. **Hassas işlevsellik:** Veri değiştirme veya kısıtlı işlemleri tetikleme.
2. **Kullanıcı verileri:** Çalınabilecek veya satılabilecek kişisel bilgiler.
3. **Yönetimsel (Admin) özellikler:** Sistemin tam kontrolünü ele geçirme.
4. **Diğer saldırı fırsatları:** İç ağda daha derine inmek veya yeni açıklar bulmak.

---

## 3. Kullanılan Araçlar ve Teknikler

### Gobuster (Gizli Dizin ve Dosya Keşfi)
Web sayfalarının ve gizli dizinlerin taranmasını otomatikleştirir.

```bash
gobuster dir --url [http://www.hedefsite.thm/](http://www.hedefsite.thm/) -w /usr/share/wordlists/dirbuster/directory-list.txt
````

- `dir`: Dizin/dosya numaralandırma (enumeration) modu.
    
- `--url`: Hedef web sitesi.
    
- `-w`: Tahmin için kullanılacak kelime listesi (wordlist).
    

### Hydra (Sözlük Saldırısı / Dictionary Attack)

Önceden tanımlanmış bir kelime listesi (wordlist) kullanarak hedef uygulamaya karşı giriş (login) denemelerini otomatikleştirir.

```bash
hydra -l admin -P passlist.txt www.hedefsite.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```
- `-l admin`: `admin` kullanıcı adı ile giriş yapmayı dener.
    
- `-P passlist.txt`: Denenecek şifrelerin bulunduğu kelime listesi dosyası.
    
- `http-post-form`: Bunun bir HTTP POST istek formu olduğunu belirtir.
    
- `-V`: Verbose (ayrıntılı) mod; denenen her kullanıcı adını ve şifreyi ekranda gösterir.