
Siber güvenlik sadece sistemleri veya ağları değil, temel olarak **dijital veriyi** korumaya odaklanır. Bu koruma, **CIA Üçlüsü (CIA Triad)** olarak bilinen üç temel ilke etrafında şekillenir. Tüm siber güvenlik stratejileri bu üç sütunun sağlam kalmasını sağlamak üzerine kuruludur.

---

## 1. Gizlilik (Confidentiality)
Hassas verilere yalnızca **yetkili kişilerin** erişebilmesini sağlar. Bilgilerin yetkisiz kişilerin eline geçmesini önler.

* **Örnek İhlaller:** Herkese açık bir Wi-Fi ağında şifrelerin çalınması, özel mesajların ortadaki adam (MitM) saldırısı ile okunması veya şirket belgelerinin internete sızdırılması.
* **Nasıl Sağlanır:** Şifreleme (Encryption) ve katı erişim kontrolleri (Access controls) kullanılarak.

---

## 2. Bütünlük (Integrity)
Verilerin **izinsiz olarak değiştirilmemesini** sağlar. Verinin doğruluğunu, güvenilirliğini ve orijinal yapısını korur.

* **Örnek İhlaller:** Bir banka havalesi sırasında alıcı hesap numarasının ağ üzerinde gizlice değiştirilmesi veya bir öğrencinin not sistemine sızıp kendi harf notunu yükseltmesi.
* **Nasıl Sağlanır:** Veri bütünlüğü kontrolleri, loglama ve sıkı yetkilendirme süreçleri ile.

---

## 3. Erişilebilirlik (Availability)
Veri ve hizmetlerin ihtiyaç duyulduğunda yetkili kullanıcılara **açık ve kullanılabilir** olmasını sağlar.

* **Örnek İhlaller:** Bir web sitesine aşırı istek gönderilerek (DDoS saldırısı) sitenin çökertilmesi, fidye yazılımı (Ransomware) nedeniyle hastane sistemlerinin kilitlenmesi veya donanım/elektrik arızaları.
* **Nasıl Sağlanır:** Yedek güç kaynakları, yük dengeleme (load balancing), yedekli donanımlar ve siber saldırı önleme sistemleri ile.

---

## 💡 Güvenlik Zihniyeti (Olay Müdahale Yaklaşımı)

Siber güvenlik sadece tanımlardan ibaret değildir; bir bakış açısıdır. Bir güvenlik ihlali veya olayı (incident) yaşandığında, profesyoneller durumu analiz etmek için olayları şu filtreden geçirir:

1. **Gizlilik Sorusu:** Hassas veriler yetkisiz kişilere ifşa edildi mi? 
2. **Bütünlük Sorusu:** Veriler izinsiz değiştirildi mi? 
3. **Erişilebilirlik Sorusu:** Sistemler veya hizmetler, kullanıcılar ihtiyaç duyduğunda kullanılamaz durumda mıydı?