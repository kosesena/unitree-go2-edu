# SWOT Analizi — Unitree Go2 EDU CE ve Siber Güvenlik Projesi

**Tarih:** 23.10.2026  
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

## O — Opportunities / Fırsatlar (dış faktörler)

| No | Fırsat | Nasıl değerlendirilecek? |
|---|---|---|
| O1 | AB Makine Tüzüğü 2023/1230 ile siber güvenlik, 20 Ocak 2027'den itibaren CE'nin ön şartı oluyor. | Projeyi tüzüğün siber güvenlik gereksinimleriyle ilişkilendir. |
| O2 | Siber Dayanıklılık Yasası (CRA) olay bildirimi ve güncelleme yükümlülükleri getiriyor. | LAB 6'da 24 saat / 72 saat / 14 gün akışını Go2 üzerinden kur. |
| O3 | Açıkları bulan araştırmacıların teknik açıklaması ve basın haberleri yayımlanmış (UniPwn, IEEE Spectrum). | Saldırı zincirini hayali değil, belgelenmiş olaylarla gerekçelendir. |
| O4 | Go2'de LLM tabanlı sesli asistan ve LiDAR ile otonom engel algılama var. | LAB 7 (AI Safety Challenge) için gerçek bir yapay zekâ örneği. |
| O5 | GitHub üzerinden sürümlü ve denetlenebilir dokümantasyon. | Her LAB ayrı commit; değişiklik geçmişi hocaya açık. |

## T — Threats / Tehditler (dış faktörler)

| No | Tehdit | Önlem |
|---|---|---|
| T1 | Unitree yeni firmware yayımlayabilir; değerlendirme eskiyebilir. | Her CVE kararını tarih ve sürümle kaydet; düzenli NVD kontrolü yap. |
| T2 | Yanlış CVE–sürüm eşleştirmesi, "robot savunmasız" gibi gerçek dışı bir iddiaya dönüşebilir. | Etkilenen sürüm doğrulanmadan "kesin etkileniyor" deme; kanıt eksiğini yaz. |
| T3 | Üreticinin AB uygunluk beyanı kamuya açık değil. | Dosyada "üretici beyanı bulunamadı" diye açıkça not et; kendi taslağımızı beyan gibi sunma. |
| T4 | Açıkların istismar kodu herkese açık; ayrıntılı saldırı adımı yazmak kötüye kullanıma yol açabilir. | Repoda yalnız etki ve önlem anlatılır; anahtar, parola veya istismar adımı yazılmaz. |
| T5 | Gerçek saha erişimi olmadan CE uygunluğunun kanıtlanmış sanılması. | Her belgede "akademik taslak" uyarısını koru. |

## SWOT'tan çıkan strateji

**SO:** Kılavuzdaki doğrulanmış bilgileri gerçek CVE kayıtlarıyla eşleyerek güçlü bir kaynak tabanı kur.  
**WO:** Firmware sürümü bilinmezliğini, tüzük ve CRA'nın istediği sürüm/güncelleme kaydı ihtiyacına bağlayarak açık bir kanıt eksiği listesiyle yönet.  
**ST:** Her zafiyet kararını tarihli tut; yeni firmware çıkarsa kararı yeniden değerlendir.  
**WT:** Fiziksel test yapılmadığı sürece gerçek CE uygunluğu veya güvenlik garantisi iddia etme; saldırı ayrıntısı paylaşma.

## Kısa sonuç

Unitree Go2 EDU; herkese açık kılavuzu, gerçek CVE kayıtları ve doğrudan fiziksel tehlike üretebilen hareketli yapısı sayesinde **akademik CE teknik dosyası** için güçlü bir örnek makinedir. En büyük kısıt, kurulu firmware sürümünün ve emniyet davranışının robot üzerinde doğrulanamamasıdır. En önemli bulgu ise emniyet fonksiyonlarının saldırıya açık olan yazılımla aynı yerde çalışmasıdır.
