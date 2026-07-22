
## Port Yönlendirme (Port Forwarding)
Port yönlendirme, yerel bir ağda çalışan uygulamaları ve hizmetleri İnternet'e (dış dünyaya) açmak için kullanılan temel bir yapılandırmadır.

- **Neden Gerekli?:** Port yönlendirme yapılmadığında, yerel ağdaki bir cihazda çalışan hizmetlere (örneğin bir web sunucusuna) yalnızca aynı ağdaki diğer cihazlar erişebilir (buna intranet denir).
- **Çalışma Mantığı:** Dış ağdaki (İnternet) bir kullanıcının, yönlendiricinin (Router) genel (public) IP adresine ve belirli bir portuna yaptığı isteği, yerel ağdaki doğru cihazın iç (private) IP adresine ve portuna yönlendirir.
- **Yapılandırma:** Bu işlem tamamen ağın yönlendiricisi (Router) üzerinde yapılandırılır.

> [!info] Güvenlik Duvarı ile Farkı
> Port yönlendirme belirli sanal kapıları (portları) dış dünyaya açma işidir. Güvenlik duvarı ise bu kapılar açık olsa bile gelen trafiğin güvenli olup olmadığını denetleme ve geçişine izin verip vermeme işidir.

---

## Güvenlik Duvarı (Firewall)
Güvenlik duvarı, bir ağa giren ve ağdan çıkan tüm trafiği kontrol etmekle görevli bir sınır güvenliği cihazıdır. 

Yöneticiler tarafından belirlenen katı kurallara göre trafiğe izin verir (**permit**) veya trafiği engeller (**deny**). Bu kararları verirken paket denetimi (packet inspection) yapar ve şu faktörleri inceler:
- Trafiğin hangi ağdan veya IP adresinden geldiği (Kaynak).
- Trafiğin hangi ağa veya IP adresine gitmek istediği (Hedef).
- Trafiğin hangi portu hedeflediği (Örn: Sadece Port 80'e izin ver gibi).
- Trafiğin hangi protokolü (TCP, UDP vb.) kullandığı.

### Güvenlik Duvarı Kategorileri

Güvenlik duvarları donanımsal (büyük şirket ağlarında) veya yazılımsal (ev yönlendiricileri veya bilgisayarlardaki yerleşik yazılımlar) olabilir. Temelde iki ana kategoriye ayrılırlar:

#### 1. Durumlu Güvenlik Duvarı (Stateful Firewall)
- Trafiği tekil paketler halinde değil, bağlantının tamamını (oturumun geçmişini ve bağlamını) inceleyerek değerlendirir.
- Karar mekanizması dinamiktir. Örneğin, kurallara uyan bir TCP el sıkışmasının ilk adımlarına izin verir ancak el sıkışmanın devamında bir gariplik sezerse bağlantıyı kesebilir.
- Kötü niyetli bir bağlantı tespit ettiğinde ilgili cihazın tüm erişimini bloklar.
- Bağlantı durumlarını sürekli takip ettiği için durumsuz duvarlara göre **çok daha fazla sistem kaynağı tüketir**.

#### 2. Durumsuz Güvenlik Duvarı (Stateless Firewall)
- Her bir veri paketini, diğer paketlerden bağımsız olarak, sabit (statik) bir kurallar dizisine göre tek tek inceler.
- Bir cihazın zararlı tek bir paket göndermesi, o cihazın tamamen engelleneceği anlamına gelmez; sadece o paket düşürülür.
- Çok az sistem kaynağı tüketir ve oldukça hızlıdır. Bu yüzden büyük ölçekli DDoS (Dağıtılmış Hizmet Reddi) saldırılarını göğüslemede çok başarılıdır.
- Ancak "aptal" bir yapıya sahiptir; esnek değildir ve paketlerin arkasındaki mantıksal bağlantıyı/bağlamı göremez.

---

## Sanal Özel Ağ (VPN)
VPN (Virtual Private Network), İnternet gibi genel ve güvensiz bir ağ üzerinde iki cihaz veya iki ağ arasında şifreli ve özel bir hat (tünel - tunnel) oluşturarak güvenli iletişim sağlayan teknolojidir.

### VPN'in Sağladığı Temel Avantajlar
- **Coğrafi Bağlantı:** Farklı konumlardaki (örneğin farklı şehirlerdeki) ofislerin ve sunucuların tek bir yerel ağdaymış gibi güvenle haberleşmesini sağlar.
- **Gizlilik (Şifreleme):** Verileri güçlü algoritmalarla şifreler. Bu sayede kafe, otel gibi şifresiz ortak Wi-Fi alanlarında verilerinizin araya giren üçüncü şahıslar tarafından dinlenmesini (sniffing) önler.
- **Anonimlik:** Trafiği kendi üzerinden geçirdiği için İnternet Servis Sağlayıcınızın (İSS) veya diğer aracıların sizi takip etmesini zorlaştırır. (Not: Kullanılan VPN servisinin veri logu tutup tutmadığı anonimlik seviyesini doğrudan etkiler).

### Temel VPN Teknolojileri ve Protokolleri

1. **PPP (Point-to-Point Protocol):** Kimlik doğrulama ve şifreleme sağlamak için kullanılan eski bir yöntemdir. Tek başına bir ağın dışına çıkma (yönlendirilme) yeteneği yoktur. Çalışmak için özel anahtar ve açık sertifika eşleşmesine ihtiyaç duyar.
2. **PPTP (Point-to-Point Tunneling Protocol):** PPP'den gelen verilerin tünellenerek ağ dışına çıkmasını ve seyahat etmesini sağlayan protokoldür. Kurulumu çok kolaydır ve neredeyse tüm cihazlar destekler ancak şifreleme kalitesi günümüz standartlarına göre oldukça zayıftır.
3. **IPSec (Internet Protocol Security):** Mevcut IP altyapısını kullanarak verileri çok güçlü bir şekilde şifreleyen gelişmiş bir protokoldür. Kurulumu ve yapılandırması karmaşıktır fakat yüksek güvenlik sunar ve yaygın olarak desteklenir.