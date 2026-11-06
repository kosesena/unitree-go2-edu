# SWOT Analizi — Unitree Go2 EDU CE ve Siber Güvenlik Projesi

**Tarih:** 23.10.2026 · **Güncelleme:** 06.11.2026 (LAB 5–7 bulguları eklendi)  
**Analizin konusu:** Unitree Go2 EDU'nun, erişilebilen kaynaklar ve akademik çalışma koşulları altında, CE teknik dosyası ve siber güvenlik incelemesi için ne kadar uygun bir makine olduğu.  
**Not:** Bu tablo bir makine test raporu değildir. Bazı değerlendirmeler benim öngörümdür ve [V] ile işaretlidir.

## S — Strengths / Güçlü yönler (iç faktörler)

| No | Güçlü yön | Projeye etkisi |
|---|---|---|
| S1 | Ayrıntılı bir kullanım kılavuzu herkese açık (IP adresleri, portlar, hesaplar, kumanda komutları, emniyet modları). | Varlık envanteri ve emniyet fonksiyonları kaynak gösterilerek [K] yazılabiliyor. |
| S2 | NVD'de Go2'yi etkileyen **5 gerçek CVE** var (Bluetooth, Wi-Fi ve firmware güncelleme yolları). | Zafiyet yönetimi uydurma değil, gerçek kayıtlar üzerinden yapılabiliyor. |
| S3 | Siber saldırı → fiziksel tehlike zinciri doğrudan kurulabiliyor: robot ≈15 kg, 5 m/s'ye kadar hız, ≈45 N·m eklem torku. | LAB 3'teki "veri çalındı ile bitmesin" kuralı doğal olarak sağlanıyor. |
| S4 | Makinede çok sayıda farklı bağlantı var: Bluetooth, Wi-Fi, 4G/eSIM, Ethernet, bulut ve el kumandası. | IEC 62443 zone/conduit çalışması (LAB 2) zengin ve somut oluyor. |
| S5 | Resmî ürün ve satış sayfaları erişilebilir. | Makine tanımı ve model ailesi (Air/Pro/X/EDU) kaynaklı olarak verilebiliyor. |

## W — Weaknesses / Zayıf yönler (iç faktörler)

| No | Zayıf yön | Azaltma yaklaşımı |
|---|---|---|
| W1 | Fiziksel robota erişim ve test kanıtı yok. | Gözlenmeyen her şeyi [V] veya "doğrulanmadı" olarak işaretle. |
| W2 | Kurulu firmware sürümü bilinmiyor; CVE'lerin bu robotu etkilediği kesin değil. | Sürüm doğrulanana kadar ihtiyatlı karar: "etkilenmiş kabul edilir" (LAB 5'te gerekçeli). |
| W3 | Kılavuz Unitree'nin değil, Almanya distribütörü MYBOTSHOP'un; bazı bölümler (port 9000 web sunucusu gibi) her Go2'de bulunmayabilir. | Distribütöre özgü bilgileri ayrıca işaretle; Unitree resmî belgeleriyle karşılaştır. |
| W4 | Ayrı bir Safety PLC olmadığı için klasik "E-stop → Safety PLC → STO" şablonu bire bir uymuyor. | Bunu eksiklik değil **bulgu** olarak yaz; föylerde Go2 karşılıklarını açıkça eşle. |
| W5 | CE teknik dosyası mekanik, elektrik, yazılım ve hukuk gibi birçok alana yayılıyor. | Çalışmayı haftalık LAB'lara ve Evidence Pack başlıklarına böl. |
| W6 | SBOM yalnız hazırlık tablosu: 13 bileşenin hiçbirinin kurulu sürümü, paket kimliği veya hash'i yok (LAB 5). | Sürüm toplama planını (EP 08) yetkili bakım sürecine bağla; sürüm gelene kadar kararları "etkilenmiş kabul" olarak tut. |
| W7 | Go2'de YZ'den ve ağdan bağımsız bir emniyet katmanı yok; LAB 7'deki fail-safe kararları bu yüzden yalnız gereksinim olarak yazılabildi. | Gereksinimi (bağımsız durdurma, PLr d) üreticiye yönelik açık eksiklik olarak kaydet; kurulmuş gibi sunma. |

## O — Opportunities / Fırsatlar (dış faktörler)

| No | Fırsat | Nasıl değerlendirilecek? |
|---|---|---|
| O1 | AB Makine Tüzüğü 2023/1230 ile siber güvenlik, 20 Ocak 2027'den itibaren CE'nin ön şartı oluyor. | Projeyi tüzüğün siber güvenlik gereksinimleriyle ilişkilendir. |
| O2 | Siber Dayanıklılık Yasası (CRA, Tüzük (AB) 2024/2847) olay bildirimi ve güncelleme yükümlülükleri getiriyor; raporlama 11.09.2026'dan itibaren geçerli. | **Yapıldı (LAB 6):** 24 saat / 72 saat / 14 gün akışı Go2 üzerinden kuruldu. |
| O3 | Açıkları bulan araştırmacıların teknik açıklaması ve basın haberleri yayımlanmış (UniPwn, IEEE Spectrum). | Saldırı zincirini hayali değil, belgelenmiş olaylarla gerekçelendir. |
| O4 | Go2'de LLM tabanlı sesli asistan ve LiDAR ile otonom engel algılama var. | **Yapıldı (LAB 7):** model hatası, manipüle girdi ve düşük güven için güvenli davranış tanımlandı. |
| O5 | GitHub üzerinden sürümlü ve denetlenebilir dokümantasyon. | Her LAB ayrı commit; değişiklik geçmişi hocaya açık. |

## T — Threats / Tehditler (dış faktörler)

| No | Tehdit | Önlem |
|---|---|---|
| T1 | Unitree yeni firmware yayımlayabilir; değerlendirme eskiyebilir. | Her CVE kararını tarih ve sürümle kaydet; düzenli NVD kontrolü yap. |
| T2 | Yanlış CVE–sürüm eşleştirmesi, "robot savunmasız" gibi gerçek dışı bir iddiaya dönüşebilir. | Etkilenen sürüm doğrulanmadan "kesin etkileniyor" deme; kanıt eksiğini yaz. |
| T3 | Üreticinin AB uygunluk beyanı kamuya açık değil. | Dosyada "üretici beyanı bulunamadı" diye açıkça not et; kendi taslağımızı beyan gibi sunma. |
| T4 | Açıkların istismar kodu herkese açık; ayrıntılı saldırı adımı yazmak kötüye kullanıma yol açabilir. | Repoda yalnız etki ve önlem anlatılır; anahtar, parola veya istismar adımı yazılmaz. |
| T5 | Gerçek saha erişimi olmadan CE uygunluğunun kanıtlanmış sanılması. | Her belgede "akademik taslak" uyarısını koru. |
| T6 | CRA bildirim yükümlülüğü üreticide (Unitree); kampüs kullanıcısı olarak bildirim zincirinin hızını ve yamanın gelişini kontrol edemiyoruz. | Kendi müdahale akışımızı (LAB 6) üreticiye kanıtlı bilgi verecek şekilde kur; yama gelene kadar telafi edici önlemleri (LAB 5) kalan risk olarak tut. |

## SWOT'tan çıkan strateji

**SO:** Kılavuzdaki doğrulanmış bilgileri gerçek CVE kayıtlarıyla eşleyerek güçlü bir kaynak tabanı kur.  
**WO:** Firmware sürümü bilinmezliğini, tüzük ve CRA'nın istediği sürüm/güncelleme kaydı ihtiyacına bağlayarak açık bir kanıt eksiği listesiyle yönet.  
**ST:** Her zafiyet kararını tarihli tut; yeni firmware çıkarsa kararı yeniden değerlendir.  
**WT:** Fiziksel test yapılmadığı sürece gerçek CE uygunluğu veya güvenlik garantisi iddia etme; saldırı ayrıntısı paylaşma.

## Kısa sonuç

**LAB 5–7 sonrası:** Beş CVE için gerekçeli karar verildi (dördü etkilenmiş kabul, biri koşullu), olay akışı ve YZ fail-safe kararları tanımlandı. Ana bulgu değişmedi; aksine güçlendi: yamanın, olay müdahalesinin ve YZ'nin güvenliği aynı yere, emniyetin normal yazılımla birlikte çalışmasına çıkıyor.

Unitree Go2 EDU; herkese açık kılavuzu, gerçek CVE kayıtları ve doğrudan fiziksel tehlike üretebilen hareketli yapısı sayesinde **akademik CE teknik dosyası** için güçlü bir örnek makinedir. En büyük kısıt, kurulu firmware sürümünün ve emniyet davranışının robot üzerinde doğrulanamamasıdır. En önemli bulgu ise emniyet fonksiyonlarının saldırıya açık olan yazılımla aynı yerde çalışmasıdır.
