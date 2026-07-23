## Windows Ağlarında Kimlik Doğrulama Protokolleri
### 1. Kerberos Protokolü 
Güncel Windows sürümlerinin varsayılan bilet tabanlı kimlik doğrulama protokolüdür.
1. **TGT (Ticket Granting Ticket) Talebi:** Kullanıcı KDC'ye başvurur. KDC kullanıcıya TGT ve Session Key verir. (TGT, `krbtgt` hesabının hash'i ile şifrelenmiştir). 
2. **TGS (Ticket Granting Service) Talebi:** Kullanıcı TGT ile KDC'ye başvurarak erişmek istediği servis için TGS bileti ister. 
3. **Servise Erişim:** Kullanıcı TGS biletini hedeflenen servise sunar ve kimliğini doğrular. 
### 2. NetNTLM Protokolü
Eski (legacy) sistemlerle uyumluluk için korunan **Challenge-Response (Sorgu-Yanıt)** mekanizmasıdır. 
- İstemci istek atar -> Sunucu rastgele bir Challenge gönderir -> İstemci NTLM hash'i ile Challenge'ı yanıtlar -> Sunucu bunu DC'ye doğrulatır. 
- Parola veya parola hash'i ağ üzerinden doğrudan iletilmez.
---  
## Çoklu Etki Alanı Yapıları 
### Ağaçlar (Trees)
Aynı ad alanını (namespace) paylaşan etki alanlarının oluşturduğu yapıdır. 
- Örnek Kök Domain: `thm.local` 
- Alt Domainler (Subdomains): `uk.thm.local`, `us.thm.local` 
- **Enterprise Admins:** Tüm ağaç ve orman genelinde tam yetkili gruptur.  
-
### Ormanlar (Forests)
Farklı ad alanlarına sahip birden fazla ağacın (Tree) birleşimiyle oluşan en üst düzey yapıdır. 
- Örnek: `thm.local` ile satın alınan `mht.com` ağaçlarının tek bir çatı altında birleşmesi.  
---  
## Güven İlişkileri (Trust Relationships)
Farklı etki alanlarındaki kullanıcıların diğer etki alanlarındaki kaynaklara erişebilmesini sağlayan köprülerdir.  
- **Tek Yönlü Güven (One-way Trust):** `Domain A` -> `Domain B` ilişkisinde, Domain B kullanıcıları Domain A kaynaklarına erişebilir. (Güven yönü erişim yönünün tersidir). 
- **Çift Yönlü Güven (Two-way Trust):** Her iki etki alanı da karşılıklı olarak birbiri kullanıcılarını yetkilendirebilir.  
- **Önemli:** Güven ilişkisi kurulması otomatik olarak her kaynağa erişim yetkisi vermez; sadece yetkilendirme altyapısını sağlar.