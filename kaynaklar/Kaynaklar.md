# Kaynaklar ve Doğrulama Durumu

**Erişim / derleme tarihi:** 23.10.2026 (CVE kayıtları 16.10.2026'da NVD'den kontrol edildi)

## Üretici, satış ve doküman kaynakları

| Kaynak | Kapsam | Durum |
|---|---|---|
| [Unitree Go2 resmî ürün sayfası](https://www.unitree.com/go2) | Model ailesi, teknik özellikler | Üretici kaynağı |
| [Unitree resmî mağaza — Go2 satış sayfası](https://shop.unitree.com/products/unitree-go2) | Satışa sunulan sürümler | 23.10.2026'da Air, Pro ve X listeleniyordu; EDU listelenmiyordu |
| [GO2 User Manual (PDF)](https://www.docs.mybotshop.de/downloads/GO2_User_Manual.pdf) | Donanım, IP adresleri, hesaplar, kumanda, emniyet modları, ROS 2 | Almanya distribütörü MYBOTSHOP'un kılavuzu; [K] etiketli bilgilerin ana kaynağı |
| [MYBOTSHOP Go2 dokümantasyonu](https://www.docs.mybotshop.de/go2.html) | Kurulum ve entegrasyon notları | Distribütör kaynağı; her Go2 için geçerli olmayabilir |
| Üreticinin AB uygunluk beyanı (DoC) | CE beyanı | **Kamuya açık bir kopya bulunamadı** |

## Güvenlik açığı kaynakları

| Kaynak | Kapsam | Durum |
|---|---|---|
| [NVD CVE-2025-35027](https://nvd.nist.gov/vuln/detail/CVE-2025-35027) | BLE Wi-Fi ayarı → root komut enjeksiyonu; Go2 ≤ 1.1.8 | Gerçek CVE; bu robota uygulanabilirliği sürüme bağlı |
| [NVD CVE-2025-60017](https://nvd.nist.gov/vuln/detail/CVE-2025-60017) | Wi-Fi SSID/parola alanından root komut enjeksiyonu | Gerçek CVE; sürüm doğrulanmadı |
| [NVD CVE-2025-60251](https://nvd.nist.gov/vuln/detail/CVE-2025-60251) | BLE el sıkışmasında zayıf kimlik doğrulama | Gerçek CVE; sürüm doğrulanmadı |
| [NVD CVE-2025-60250](https://nvd.nist.gov/vuln/detail/CVE-2025-60250) | BLE'de sabit şifreleme anahtarı/IV | Gerçek CVE; sürüm doğrulanmadı |
| [NVD CVE-2026-1442](https://nvd.nist.gov/vuln/detail/CVE-2026-1442) | Firmware güncellemelerinin değiştirilebilmesi | Gerçek CVE; yerel erişim ve kullanıcı etkileşimi gerektiriyor (AV:L/UI:R) |
| [UniPwn — araştırmacıların açıklaması](https://github.com/Bin4ry/UniPwn) | Açıkların teknik arka planı (A. Makris, K. Finisterre, Eylül 2025) | Yalnızca referans; repoda istismar adımı kullanılmadı |
| [IEEE Spectrum haberi](https://spectrum.ieee.org/unitree-robot-exploit) | Açıkların etkisi ve üretici yanıtı | İkincil kaynak |

## Ders materyali

| Kaynak | Kullanım |
|---|---|
| Safety 4.0 Bootcamp Laboratuvar Föyleri — Genel Sürüm | `docs/` içindeki PDF'nin şablonu |
| Ders sunumu (Evidence Pack 15 başlık, risk puanlama L × S × E) | Föy cevaplarının yöntemi |

## CVE değerlendirme kaydı (özet)

- **Etkilenen ürünler:** Go2, G1, H1, B2 (ortak firmware)
- **Etkilenen sürüm:** CVE-2025-35027 kaydına göre Go2 firmware 1.1.8 ve öncesi
- **Makinemize uygulanabilirlik:** **Bilinmiyor**. Kurulu firmware sürümü doğrulanmalı. Doğrulanana kadar ihtiyatlı karar: *etkilenmiş kabul edilir*.
- **Yama durumu:** Unitree açığı kabul edip düzeltmenin geleceğini duyurdu. Düzeltilmiş sürümü doğrulayan resmî bir kaynak bulunamadı.
- **Gerekli kanıt:** Kurulu firmware sürümü, Bluetooth/Wi-Fi yapılandırması, güncelleme kayıtları, ağ erişilebilirliği.

Bu sayfadaki bilgiler, belirli bir Go2'de güvenlik açığı bulunduğu iddiası değildir. Anahtar, parola veya istismar adımı bu repoya yazılmamıştır.
