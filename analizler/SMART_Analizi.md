# SMART Analizi — Unitree Go2 EDU Projesi

**Başlangıç tarihi:** 23.10.2026  
**Planlama ufku:** 8 hafta. Bu takvim benim önerdiğim proje takvimidir; dersin resmî teslim tarihi henüz doğrulanmadı.

## Ana SMART hedefi

**23 Ekim – 18 Aralık 2026** arasında Unitree Go2 EDU için LAB 1–7 föylerini tamamlamak, Evidence Pack'in 15 başlığını en az **Taslak** durumuna getirmek, NVD'deki 5 CVE'nin her biri için gerekçeli bir etkilenme kararı vermek ve kaynakları ile eksikleri açıkça belirtilmiş **bir akademik CE teknik dosya taslağı** hazırlamak.

### SMART ölçütleri

| Harf | Ölçüt | Projeye uygulaması |
|---|---|---|
| **S** | Specific — Belirli | Tek model (Go2 EDU), tek kullanım senaryosu (kampüs devriye robotu), emniyet fonksiyonları, ağ bağlantıları, CVE'ler ve CE teknik dosya taslağı. |
| **M** | Measurable — Ölçülebilir | 7 LAB föyü, 15 Evidence Pack başlığı, 5 CVE kararı, en az 3 risk senaryosu, 1 zone/conduit şeması, en az 5 kaynak kaydı. |
| **A** | Achievable — Ulaşılabilir | Herkese açık kılavuz, NVD kayıtları ve masa başı analizle yapılabilir; fiziksel test iddiası yok. |
| **R** | Relevant — İlgili | Makine Tüzüğü 2023/1230 ve CRA'nın siber güvenlik şartlarını gerçek bir robota uygular; dersin LAB akışıyla birebir örtüşür. |
| **T** | Time-bound — Zamanlı | Haftalık LAB teslimleri; önerilen bitiş 18.12.2026. Ders takvimi netleşince güncellenir. |

## İş paketleri ve başarı ölçütleri

| Hedef | Önerilen bitiş | Ölçülebilir teslim | Başarı ölçütü |
|---|---|---|---|
| H1 — LAB 1–4 | 23.10.2026 ✅ | Kapak + 4 föy (PDF, 5 sayfa) | Her soru Go2'ye göre cevaplı; bilgiler [K]/[CVE]/[V] ile ayrılmış. |
| H2 — LAB 5 (SBOM / CVE / Patch) | 30.10.2026 | 1 föy + yazılım envanteri | 5 CVE için "bileşen var mı / sürüm etkileniyor mu / ulaşılabilir mi" tablosu dolu. |
| H3 — LAB 6 (CRA Incident) | 06.11.2026 | 1 föy + olay müdahale akışı | 24 s / 72 s / 14 gün adımlarının her biri için sorumlu ve korunacak kayıt yazılı. |
| H4 — LAB 7 (AI Safety) | 13.11.2026 | 1 föy + AI fail-safe kararı | LLM ve LiDAR engel algılama için arıza durumunda güvenli davranış tanımlı. |
| H5 — Evidence Pack 10–15 | 04.12.2026 | Eksik 6 başlık (zafiyet kaydı, yama, yedekleme, olay müdahalesi, değişiklik yönetimi, doğrulama) | 15 başlığın tamamı en az Taslak durumda. |
| H6 — Gözden geçirme ve teslim | 18.12.2026 | Revize teknik dosya + kontrol listesi | Kaynağı olmayan kesin iddialar temizlenmiş; tüm bağlantılar çalışıyor. |

## İzleme tablosu

| Gösterge | Hedef | Durum (23.10.2026) |
|---|---:|---|
| Tamamlanan LAB föyü | 7 | 4 (LAB 1–4) |
| Evidence Pack başlığı (en az Taslak) | 15 | 9 (01–09) + 10 kısmen |
| CVE etkilenme kararı | 5 | 5 karar taslağı var; firmware sürümü doğrulanmadı |
| Risk senaryosu | ≥ 3 | 3 (R-01, R-02, R-03) |
| Zone/conduit şeması | 1 | 1 (Z0–Z3, C1–C7) |
| Kaynak kaydı | ≥ 5 | 11 (bkz. `kaynaklar/Kaynaklar.md`) |

## Kapsam dışında

Gerçek robotta sızma testi, emniyet doğrulama deneyi, bağımsız belgelendirme, üretici adına AB uygunluk beyanı düzenlemek ve resmî CE işaretlemesi.

> Not: Takvimdeki tarihler proje yönetimi için önerdiğim **hedef** tarihlerdir; hocanın belirlediği resmî teslim tarihleri olarak sunulmaz.
