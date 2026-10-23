# Proje Kapsamı ve CE Teknik Dosyası Hazırlık Notları

## Seçilen makine

**Unitree Robotics Go2 EDU dört bacaklı mobil robot.** İncelenen şey belirli bir seri numaralı robot değil, kamuya açık üretici ve distribütör belgeleri üzerinden ele alınan modeldir.

## Kullanım senaryosu (varsayım)

Go2 EDU bir üniversitede **kampüs içi devriye ve araştırma robotu** olarak kullanılıyor: koridorlarda insanların arasında otonom dolaşıyor, kamera görüntüsü aktarıyor, kampüs Wi-Fi'ına bağlı ve araştırmacılar SSH ile bağlanıp ROS 2 paketleri yüklüyor.

## Verilerin sınıflandırılması

- **Doğrulandı [K]/[CVE]:** Kılavuzdaki donanım, IP adresleri, portlar, hesaplar, kumanda komutları ve emniyet modları; NVD'de Go2'yi etkilenen ürün sayan 5 CVE kaydı.
- **Henüz bilinmiyor:** Kurulu firmware sürümü, takılı opsiyonlar, gerçek ağ yapılandırması, emniyet fonksiyonlarının gerçek davranışı, üreticinin AB uygunluk beyanı.
- **Akademik tasarım önerisi [V]:** Ağ bölgelendirme (Z0–Z3), erişim kuralları, uzak erişim prosedürü, rol matrisi. Bunlar robotta kurulu olarak iddia edilmez.

## Evidence Pack — 15 başlık ve durum

| # | Başlık | İlgili LAB | Durum |
|---|---|---|---|
| 01 | Asset Inventory | LAB 2 | Taslak |
| 02 | Network Architecture | LAB 2 / LAB 4 | Taslak |
| 03 | Safety Functions | LAB 1 | Taslak |
| 04 | Cyber Risk Assessment | LAB 3 | Taslak |
| 05 | Zone & Conduit | LAB 2 | Taslak |
| 06 | Remote Access Procedure | LAB 4 | Taslak |
| 07 | User/Role Matrix | LAB 2 | Taslak |
| 08 | Software/Firmware Inventory | LAB 5 | Taslak |
| 09 | SBOM | LAB 5 | Taslak |
| 10 | Vulnerability Records | LAB 5 | Kısmen |
| 11 | Patch/Update Records | LAB 5 | Yok |
| 12 | Backup & Restore | — | Yok |
| 13 | Incident Response | LAB 6 | Yok |
| 14 | Change Management | — | Yok |
| 15 | Verification/Test | — | Yok |
| + | AI Fail-Safe Decision | LAB 7 | Yok |

Bu repoda şimdilik yalnızca LAB 1–4 föyleri yayımlanmıştır. Evidence Pack başlıkları ders ilerledikçe ilgili LAB ile birlikte eklenecektir.

## Kritik sınır

Resmî uygunluk dosyası; üreticinin teknik ölçümlerini, çizimlerini, risk değerlendirmesini ve mevzuatın istediği diğer kanıtları gerektirir. Bu GitHub reposu bunların yerine geçmez.

## Föy ile ilişkinin sınırı

`docs/` içindeki PDF **yalnızca kapak + LAB 1–4 (toplam 5 sayfa)** içerir. LAB 5, LAB 6 ve LAB 7 henüz eklenmemiştir; ders ilerledikçe aynı PDF'ye sırayla eklenecektir. Haftalık föyler ile dönem sonu CE teknik dosyası **aynı teslim değildir**; repo teknik dosya çalışmasıyla ayrıca genişletilebilir.
