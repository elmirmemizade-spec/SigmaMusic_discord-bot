# 📋 SigmaMusic Değişiklik Günlüğü

> ⚠️ **Bu kod umutxyp'ye aittir. Sadece kod üzerinde düzenleme ve yenileme gerçekleştirilmiştir.**

---

## v16.0.1 — Güncelleme Notları

### 🐛 Hata Düzeltmeleri

- **YouTube Format Düzeltmesi**
  - `format: 'bestaudio'` seçeneği artık YouTube'un yeni koruma sistemiyle uyumsuz hale geldiği için güncellendi.
  - Yeni format sırası: `bestaudio[ext=webm] / bestaudio[ext=m4a] / bestaudio / best` — mevcut formatlardan en uygununu otomatik seçer.
  - Bu değişiklik `Requested format is not available` hatasını çözer.

### 🔐 Güvenlik & Kimlik Doğrulama

- **Cookie Desteği Eklendi**
  - YouTube'un bot algılama sistemine karşı `cookies.txt` dosyası desteği `downloadTrack` fonksiyonuna entegre edildi.
  - `COOKIES_FILE=./cookies.txt` ortam değişkeniyle yapılandırılabilir.
  - "Sign in to confirm you're not a bot" hatası artık cookie ile aşılabiliyor.

- **User-Agent Güncellendi**
  - Eski genel User-Agent yerine Chrome 131 tabanlı güncel User-Agent tanımlandı.
  - YouTube ve diğer platformlar tarafından bot olarak işaretlenme riski azaltıldı.

### 🎨 Arayüz Güncellemeleri

- **Müzik Seçme Arayüzü Yenilendi**
  - Şarkı arama ve seçme ekranı yeniden tasarlandı.
  - Daha temiz ve anlaşılır bir görünüm sağlandı.
  - Kullanıcıların şarkıları daha hızlı bulup seçebilmesi için arayüz sadeleştirildi.

### ⚡ Performans İyileştirmeleri

- **Müzik Seçimi Optimizasyonu**
  - Şarkı arama ve sıraya ekleme işlemleri optimize edildi.
  - Daha hızlı çalma başlatma süresi sağlandı.
  - Arka planda ön indirme (preload) sistemi daha verimli çalışacak şekilde iyileştirildi.

---

## Kurulum Sonrası Yapılması Gerekenler

Bu güncellemeyi uyguladıktan sonra:

1. `cookies.txt` dosyasını `index.js` ile aynı klasöre koy
2. `.env` dosyasına şunu ekle:
   ```env
   COOKIES_FILE=./cookies.txt
   ```
3. Botu yeniden başlat:
   ```bash
   npm start
   ```

---

*SigmaMusic v16.0.1 — Güncelleme tarihi: Mart 2026*
