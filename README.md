# Unitree Go2 EDU Dört Bacaklı Robot — CE ve Siber Güvenlik İncelemesi

**Ders:** Yazılım Mühendisliğinde Güncel Konular  
**Hazırlayan:** Sena Köse (235542006)  
**Grup:** B Şubesi  
**Tarih:** 23.10.2026  
**Durum:** Kapak + LAB 1–4 tamamlandı. Sonraki laboratuvarlar her hafta eklenecek.

## Projenin amacı

Gerçek ve ticari olarak satılan bir makine olan **Unitree Go2 EDU dört bacaklı mobil robotu** teknik dokümantasyon, makine emniyeti ve siber güvenlik açısından değerlendirmek. Amaç, **siber bir açığın fiziksel bir tehlikeye nasıl dönüştüğünü** göstermek ve dönem sonunda CE uygunluk değerlendirmesine yardımcı olabilecek **akademik bir teknik dosya taslağı** hazırlamak.

Go2'yi seçmemin nedeni şu: Robot Bluetooth, Wi-Fi ve 4G üzerinden kontrol ediliyor, insanların arasında 5 m/s'ye kadar hızla hareket edebiliyor ve NVD'de kayıtlı gerçek CVE'leri var. Bu yüzden siber güvenlikten fiziksel zarara uzanan zincir somut olarak kurulabiliyor.

> Bu repo gerçek bir CE belgesi, AB uygunluk beyanı veya robotun güvenli olduğuna dair bir test garantisi **değildir**. Fiziksel robota erişim yoktur; robot üzerinde tarama, istismar veya test yapılmamıştır. Robotun kurulu firmware sürümü doğrulanmadığı için gerçek durumu hakkında kesin ifade kullanılmaz.

## İçerik

| Dosya | Açıklama |
| --- | --- |
| [`docs/Unitree_Go2_Laboratuvar_Foyu.pdf`](docs/Unitree_Go2_Laboratuvar_Foyu.pdf) | **Ana föy (Genel Sürüm şablonu):** Kapak + LAB 1–4, Go2'ye göre doldurulmuş (5 sayfa). LAB 5–7 bu aşamada yok. |
| [`docs/Unitree_Go2_Laboratuvar_Foyu_PaketPro.pdf`](docs/Unitree_Go2_Laboratuvar_Foyu_PaketPro.pdf) | **Ek föy (PaketPro 3000 şablonu):** Aynı LAB 1–4, PaketPro sorularıyla (5 sayfa). PaketPro'ya özgü iki soru Go2 karşılığıyla cevaplandı: LAB 2-S2 "uzak bakım modülü" → 4G/eSIM + bulut bağlantısı; LAB 4-B2 "ışık perdesi zinciri" → LiDAR engel algılama + kumanda acil durdurma. |
| [`analizler/SWOT_Analizi.md`](analizler/SWOT_Analizi.md) | Projenin ve seçilen makinenin güçlü/zayıf yönleri, fırsatlar ve tehditler. |
| [`analizler/SMART_Analizi.md`](analizler/SMART_Analizi.md) | Belirli, ölçülebilir, ulaşılabilir, ilgili ve zaman sınırlı proje hedefleri. |
| [`kaynaklar/Kaynaklar.md`](kaynaklar/Kaynaklar.md) | Üretici sayfası, satış sayfası, kullanım kılavuzu ve CVE kayıtları; kanıt durumu. |
| [`PROJE_KAPSAMI.md`](PROJE_KAPSAMI.md) | Kapsam, kullanım senaryosu, varsayımlar ve teknik dosyanın sonraki adımları. |
| [`HAFTALIK_ILERLEME.md`](HAFTALIK_ILERLEME.md) | Hangi LAB'ın tamamlandığı ve güncelleme kuralı. |

## İncelenen makine

- **Üretici / model:** Unitree Robotics — Go2 EDU (Go2 ailesi: Air, Pro, X, EDU)
- **Makine türü:** Dört bacaklı (quadruped) mobil robot
- **Resmî ürün sayfası:** https://www.unitree.com/go2
- **Satış sayfası (resmî mağaza):** https://shop.unitree.com/products/unitree-go2. 23.10.2026'da mağazada Air, Pro ve X sürümleri listeleniyordu. **EDU sürümü mağazada yoktu**; EDU, Unitree satış ekibi veya yetkili distribütör üzerinden satılıyor.
- **Kullanım kılavuzu:** [GO2 User Manual (MYBOTSHOP, Almanya distribütörü)](https://www.docs.mybotshop.de/downloads/GO2_User_Manual.pdf)
- **Kılavuzdan doğrulanan varlıklar:** ≈15 kg gövde ve 12 eklem motoru, MCU (192.168.123.161), dahili bilgisayar (192.168.123.18), dahili router (192.168.123.100), 4D LiDAR L1, HD kamera, 15.000 mAh batarya, el kumandası, Bluetooth 5.2, Wi-Fi 6, 4G/eSIM, Ethernet/USB portları
- **Bilinmeyenler:** Seri numarası, kurulu firmware sürümü, takılı opsiyonlar (ör. Jetson Orin), gerçek ağ yapılandırması, üreticinin AB uygunluk beyanı (internette bulunamadı)

## Varsayılan kullanım senaryosu

Go2 EDU, bir üniversitenin mühendislik fakültesinde **kampüs içi devriye ve laboratuvar araştırma robotu** olarak kullanılıyor. Koridorlarda öğrencilerin arasında otonom dolaşıyor, kamerasından görüntü aktarıyor, kampüs Wi-Fi'ına bağlı. Araştırmacılar robota SSH ile bağlanıp kod yüklüyor. *(Bu senaryo bir varsayımdır [V].)*

## Ana bulgu

Go2'de **ayrı bir emniyet kontrol sistemi (Safety PLC / bağımsız E-stop yolu) yok**. Acil durdurma, engel algılama, hız sınırı ve denge koruması dahil bütün emniyet fonksiyonları, normal hareketi yöneten yazılımın içinde çalışıyor. Saldırgan bu yazılımı ele geçirirse emniyet fonksiyonları da etkilenebilir (bkz. PDF, LAB 1 ve LAB 4).

## Güvenlik açığı incelemesi

NVD'de Go2'yi etkilenen ürünler arasında sayan beş kayıt var (16.10.2026'da kontrol edildi):

| CVE | Konu | CVSS 3.1 |
|---|---|---|
| [CVE-2025-35027](https://nvd.nist.gov/vuln/detail/CVE-2025-35027) | BLE ile Wi-Fi ayarı sırasında komut enjeksiyonu → root | 7.3 |
| [CVE-2025-60017](https://nvd.nist.gov/vuln/detail/CVE-2025-60017) | Wi-Fi SSID/parola alanından root komut enjeksiyonu | 8.2 |
| [CVE-2025-60251](https://nvd.nist.gov/vuln/detail/CVE-2025-60251) | BLE el sıkışmasında zayıf parola kontrolü | 5.0 |
| [CVE-2025-60250](https://nvd.nist.gov/vuln/detail/CVE-2025-60250) | BLE paketlerinde sabit, herkesçe bilinen anahtar/IV | 4.7 |
| [CVE-2026-1442](https://nvd.nist.gov/vuln/detail/CVE-2026-1442) | Firmware güncellemelerinin değiştirilebilmesi | 7.8 |

CVE-2025-35027 kaydına göre Go2 firmware **1.1.8 ve öncesi** etkileniyor. **Bu açıkların belirli bir Go2'yi etkilediği kanıtlanmış değildir**; önce kurulu firmware sürümü doğrulanmalıdır. Düzeltilmiş sürümü doğrulayan resmî bir kaynak bulunamadı.

## Çalışma ilkeleri

1. Bilgileri etiketle: **[K]** kılavuzdan doğrulandı · **[CVE]** NVD kaydından doğrulandı · **[V]** varsayım.
2. Robot üzerinde izinsiz tarama, istismar veya ayar değişikliği yapma.
3. Emniyet fonksiyonlarıyla ilgili çıkarımları test sonucu gibi sunma.
4. Gerçek CE uygunluğu beyan etme; akademik teknik dosya taslağı üret.
5. Yeni kaynak ve kanıtları tarih ve sürüm bilgisiyle ekle.

## Haftalık güncelleme yöntemi

- **Mevcut sürüm:** Kapak + LAB 1, LAB 2, LAB 3 ve LAB 4 (5 sayfa), iki şablonla: Genel Sürüm (ana föy) ve PaketPro 3000 (ek föy).
- **LAB 5 işlendiğinde:** Önceki sayfalar korunur, tamamlanan LAB 5 sayfası iki PDF'nin de sonuna eklenir ve yeni bir commit olarak yayımlanır.
- **LAB 6 ve LAB 7:** Aynı şekilde, yalnızca tamamlandıktan sonra eklenir.
- **SWOT ve SMART:** Yeni bulgular geldikçe güncellenir.
- **Commit mesajı:** Eklenen LAB'ı ve tarihi içerir (ör. `docs: LAB 5 eklendi (30.10.2026)`).

| Bölüm | Repo durumu |
| --- | --- |
| Kapak ve LAB 1–4 | Tamamlandı / PDF'de |
| LAB 5 | Henüz eklenmedi |
| LAB 6 | Henüz eklenmedi |
| LAB 7 | Henüz eklenmedi |

## Planlanan devam

Firmware/yazılım envanteri ve SBOM (LAB 5) → olay müdahale akışı (LAB 6) → yapay zekâ özelliği (LLM, LiDAR engel algılama) için fail-safe kararı (LAB 7) → kanıt matrisi → akademik CE teknik dosya taslağı.
