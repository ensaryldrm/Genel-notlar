## 1. Shodan (İnternet Arama Motoru)
Shodan, yalnızca Nesnelerin İnterneti (IoT) cihazları için değil; ağ ekipmanları, endüstriyel kontrol sistemleri ve kameralar dahil internete açık her şeyi sürekli tarayan bir arama motorudur.

* **Kullanım Amacı:** Belirli bir sürümün hangi sunucularda çalıştığını (örn. `apache 2.4.1`) ülke, port ve organizasyon bazında görmek.
* **Faydalı Sorgu Filtreleri:**
  * `country`: Belirli bir ülkeyi kısıtlar (Örn: `country:IE`)
  * `port`: Belirli bir porta göre filtreler (Örn: `port:22`)
  * `org`: Belirli bir kuruma veya ASN'ye göre sınırlar (Örn: `AS7224`)
  * `hostname`: Belirli bir alan adı ile eşleştirir (Örn: `hostname:fakebank.thm`)

---

## 2. VirusTotal
70'ten fazla antivirüs motorunu ve web sitesi tarayıcısını tek bir arayüzde birleştiren popüler bir analiz platformudur.

* **Ne İşe Yarar:** Bir dosya, URL, domain veya file hash değeri göndererek zararlı olup olmadığını (kötü amaçlı yazılım konsensüsünü) hızlıca görmenizi sağlar.
* **Kullanım Yeri:** Mavi takım (Blue Team) topluluğunda şüpheli bağlantıları ve dosyaları doğrulamak için sıkça kullanılır.

---

## 3. CVE (Common Vulnerabilities and Exposures) ve Zafiyet Sözlükleri
CVE, endüstrinin bilinen güvenlik açıkları için evrensel sözlüğüdür.

* **Format:** `CVE-YIL-NUMARA` (Örn: `CVE-2025-55182`)
* **Önem Puanı (CVSS):** Etki (Impact), Karmaşıklık (Complexity) ve Erişilebilirlik (Availability) gibi kriterlere göre puanlanarak risk önceliği belirlenmesini sağlar.
* **ExploitDB:** Zafiyetlerin detaylarını ve çalıştırılabilir "Kavram Kanıtı (PoC - Proof of Concept)" betiklerini barındırır.

---

## 4. GitHub ve PoC Araştırmaları
Araştırmacılar, en son tehditler ve zafiyetler için GitHub üzerinde hızlıca raporlar ve PoC kodları yayınlarlar.

* **Arama:** Doğrudan bir CVE kodu (örn. `CVE-2026-1337`) aratılarak ilgili tarayıcı script'leri veya analiz depoları bulunabilir.
* **Güvenlik Uyarısı:** Her PoC güvenilir olmayabilir; eksik, kusurlu veya zararlı (malicious) içerebilir. Çalıştırmadan önce mutlaka kodlar incelenmelidir.

---

## 5. Yerleşik Belgeler ve MAN Sayfaları
Üçüncü taraf eğitimler yerine her zaman resmi araç dokümantasyonları ve terminal kılavuzları ilk başvuru kaynağı olmalıdır.

* **MAN Sayfaları:** Linux terminalinde komutlar ve araçlar hakkında detaylı dokümantasyon sunar.
  * *Kullanım:* `man <komut>` (Örn: `man nc`)