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
| 10 | Vulnerability Records | LAB 5 | Taslak — 5 CVE için var / sürüm / ulaşılabilir kararı (LAB 5, PDF s.6); kurulu sürüm doğrulanmadı |
| 11 | Patch/Update Records | LAB 5 | Kısmen — önce test, sonra yama yaklaşımı ve telafi edici önlemler (LAB 5); gerçek yama kaydı yok, düzeltilmiş sürüm bulunamadı |
| 12 | Backup & Restore | — | Yok |
| 13 | Incident Response | LAB 6 | Taslak — 15 dk / 2 s / 24 s / 72 s / 14 gün olay akışı (LAB 6, PDF s.7) |
| 14 | Change Management | — | Yok |
| 15 | Verification/Test | LAB 5 / LAB 7 | Kısmen — yama sonrası SF-1…SF-5 yeniden test gereği (LAB 5) ve YZ arızalarında doğrulanacak güvenli davranışlar (LAB 7); test planı/sonucu yok |
| + | AI Fail-Safe Decision | LAB 7 | Taslak — üç arıza durumu için karar tablosu (LAB 7, PDF s.8); güven eşiği 0,90 varsayım [V] |

**Durum (06.11.2026):** LAB 1–7 föylerinin hepsi yayımlandı. 15 başlıktan 11'i (01–10, 13) en az Taslak, 2'si (11, 15) kısmen; 12 Backup & Restore ve 14 Change Management henüz yok. Bu başlıkların föyde karşılığı olmadığı için dönem sonu teknik dosyasında ayrıca yazılacak.

## Kritik sınır

Resmî uygunluk dosyası; üreticinin teknik ölçümlerini, çizimlerini, risk değerlendirmesini ve mevzuatın istediği diğer kanıtları gerektirir. Bu GitHub reposu bunların yerine geçmez.

## Föy ile ilişkinin sınırı

`docs/` içindeki iki PDF (Genel Sürüm ve PaketPro 3000 şablonu) **kapak + LAB 1–7 (her biri 8 sayfa)** içerir. LAB 1–4 22.10.2026'da, LAB 5–7 06.11.2026'da eklendi. Haftalık föyler ile dönem sonu CE teknik dosyası **aynı teslim değildir**; repo teknik dosya çalışmasıyla ayrıca genişletilebilir.
