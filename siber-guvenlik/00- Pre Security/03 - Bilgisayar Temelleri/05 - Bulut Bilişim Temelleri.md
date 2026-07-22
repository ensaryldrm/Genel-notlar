## 1. Bulut Bilişimin Temel Faydaları ve Özellikleri

Bulut, sınırlı kapasite ve yüksek maliyet gibi geleneksel donanım sorunlarını şu özellikleriyle çözer:
* **Ölçeklenebilirlik (Scalability):** İhtiyaçlar değiştikçe sistem kaynaklarını kolayca büyütme veya küçültme yeteneği.
* **İsteğe Bağlı Self Servis (On-demand Self-service):** Donanım beklemeksizin anında sunucu ve depolama alanı oluşturabilme.
* **Kullandığın Kadar Öde (Pay-as-you-go):** Sabit ön maliyetler yerine sadece kullanılan kaynak kadar ücretlendirme.
* **Güvenlik (Security):** Bulut sağlayıcıları tarafından sunulan güçlü kurumsal güvenlik önlemleri.
* **Yüksek Erişilebilirlik (High Availability):** Sistemin bir parçası arızalansa bile uygulamanın çalışmaya devam etmesi.
* **Küresel Erişim (Global Access):** Dünyanın her yerinden kullanıcılara hızlı ve kesintisiz hizmet sunabilme.

---

## 2. Bulut Dağıtım Türleri

İhtiyaç duyulan kontrol ve gizlilik seviyesine göre üç ana bulut ortamı vardır:
* **Genel Bulut (Public Cloud):** Altyapının bulut sağlayıcısına ait olduğu, kaynakların internet üzerinden birden fazla kullanıcı/şirket tarafından paylaşıldığı modeldir (Örn: Çoğu web sitesi ve startup).
* **Özel Bulut (Private Cloud):** Sadece tek bir şirkete veya kuruma özel olarak kurulan, kontrol ve güvenliğin maksimum olduğu bulut modelidir (Örn: Bankalar, devlet kurumları).
* **Hibrit Bulut (Hybrid Cloud):** Genel ve özel bulutun birleşimidir. Hassas veriler özel bulutta tutulurken, trafik yoğunluğunda genel bulutun ölçeklenebilirliğinden faydalanılır.

---

## 3. Bulut Hizmet Modelleri

Kullanıcının yönetmek istediği sorumluluk seviyesine göre ayrılır (Bir evi nasıl kiraladığınıza benzer):

* **IaaS (Hizmet olarak Altyapı):** Sunucu, depolama ve ağ gibi temel donanım kaynaklarını kiralarsınız. İşletim sistemini ve uygulamayı **siz yönetirsiniz**.
* **PaaS (Hizmet olarak Platform):** Altyapıyı ve işletim sistemini sağlayıcı yönetir. Siz sadece kod yazmaya ve **uygulamanızı çalıştırmaya odaklanırsınız**.
* **SaaS (Hizmet olarak Yazılım):** Her şeyin sağlayıcı tarafından yönetildiği, internet üzerinden doğrudan kullanılan **hazır yazılımlardır** (Örn: Gmail, Zoom).

---

## 4. Başlıca Bulut Sağlayıcıları ve Kullanım Örnekleri

* **Amazon Web Services (AWS):** En popüler ve sektör lideri bulut sağlayıcısı.
* **Microsoft Azure:** Özellikle kurumsal ve hibrit çözümlerde güçlü.
* **Google Cloud Platform (GCP):** Veri analitiği ve makine öğreniminde öne çıkar.
* Diğerleri: **Oracle Cloud**, **Alibaba Cloud**, **IBM Cloud**.

> **Gerçek Dünya Örnekleri:**
> * **Netflix:** Küresel ölçekte milyonlarca kullanıcıya anlık yayın yapmak için AWS kullanır.
> * **Spotify & Instagram:** Devasa veri depolama ve anlık trafik artışlarını yönetmek için buluta güvenir.

---

## 5. Temel Bulut Terminolojisi (AWS Örneği)

Bulut platformlarında (örneğin AWS) kaynak oluştururken karşımıza çıkan temel terimler:
* **EC2 (Sanal Sunucu):** AWS bulutundaki sanal bilgisayarlardır (Instance). İşlemcisi, RAM'i vardır ve uygulama çalıştırır.
* **Örnek Türü (Instance Type):** Sanal bilgisayarın gücünü (CPU/RAM) belirler (Örn: `t3.micro`, `m5.large`). Daha büyük örnekler daha fazla güç ancak daha yüksek maliyet demektir.
* **Bölge (Region):** Bulut sunucularının fiziksel olarak bulunduğu coğrafi konumdur (Örn: Avrupa, Kuzey Amerika).
* **Maliyet Optimizasyonu (Billing):** Bulutta sadece çalışan makineler için ödeme yaparsınız. Kullanılmayan test makinelerini durdurmak (Stop) maliyetleri anında ve önemli ölçüde düşürür.