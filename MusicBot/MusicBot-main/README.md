> ⚠️ **Bu kod umutxyp'ye aittir. Sadece kod üzerinde düzenleme ve yenileme gerçekleştirilmiştir.**

<div align="center">

# SigmaMusic v16.0 🎶

![GitHub Yıldızları](https://img.shields.io/github/stars/umutxyp/musicbot?style=social)
![GitHub Çatalları](https://img.shields.io/github/forks/umutxyp/musicbot?style=social)
![GitHub Sorunları](https://img.shields.io/github/issues/umutxyp/musicbot)
![GitHub Lisansı](https://img.shields.io/github/license/umutxyp/musicbot)

## Proje Özellikleri
| Özellik | Detay |
| --- | --- |
| 🎛️ Dinamik Embed'ler | Kapak resmi, platform rozeti, kuyruk sayacı ve yerelleştirilmiş meta veri içeren otomatik yenilenen "Şimdi Çalıyor" kartları. |
| 🪄 Akıllı Kuyruk | Anlık ekleme, sıralı ön yükleme, DJ kısıtlamalı karıştırma ve kanalları düzenli tutmak için çalma listesi daraltma. |
| 🔁 Döngü Modları | Üç yönlü döngü: Kapalı, Parça Tekrar (mevcut şarkıyı süresiz çal) veya Kuyruk Tekrar (kuyruk bittiğinde başa dön). |
| 🎲 Otomatik Oynatma | 20 farklı tür seçeneğiyle akıllı içerik filtrelemeli otomatik oynatma — Pop, Rock, Hip-Hop, Anime, Lo-Fi ve daha fazlası. |
| 💾 Yerel Ses Önbelleği | Tüm parçalar yerel olarak önceden indirilip önbelleğe alınır; bu sayede akış kesintileri, ağ gecikmesi ve ses kırılmaları ortadan kalkar. |
| 🛡️ Dayanıklı Oynatma | Ses bağlantısı izleme, akış yeniden deneme mantığı, boşta otomatik bağlantı kesme ve düzgün SIGINT kapatma. |
| 🧠 Çoklu Dil | `node-json-db` ile önbelleğe alınmış çeviriler, çalışma zamanında dil değiştirme ve yedek mantık. |
| 📜 Sözler | Genius'tan sözler çekimi (web kazıma) ve LRCLIB yedeklemesi — sayfalama destekli buton tabanlı görüntüleme. |
| ⚙️ Genişletilebilir Çekirdek | Modüler sağlayıcılar (`src/YouTube.js`, `src/Spotify.js`, `src/SoundCloud.js`, `src/DirectLink.js`) ile hızlıca yeni kaynaklar eklenebilir. |

</div>

---

## ✨ Neden SigmaMusic?

- **Slash-öncelikli UX** – `/play`, `/search`, `/language`, `/nowplaying` ve `/help` komutları yerelleştirilmiş embed'ler ve canlı güncellemeli butonlarla anında yanıt verir.
- **Çok Platform Desteği** – YouTube, Spotify, SoundCloud veya doğrudan MP3/WAV/OGG bağlantısından akış sağlar. Spotify albümleri, çalma listeleri ve sanatçı radyoları tam kuyruklara dönüştürülür.
- **Uyarlanabilir Arayüz** – İki satırlı kontrol paneli (Duraklat, Atla, Durdur, Kuyruk, Karıştır, Ses) ses motoruyla senkronize kalır.
- **Gelişmiş Ses Çekirdeği** – Tüm kuyruğu önceden yükler, ses bağlantısını onarır ve Discord veya üçüncül servisler aksaklık yaşadığında sorunsuz devam eder.
- **Global Ses** – 21 tam çevrilmiş dil paketiyle gelir ve anında sunucu bazında değiştirilebilir.
- **Gizlilik Odaklı** – Yalnızca sunucu başına dil tercihini yerel bir JSON veritabanında saklar. Sohbet kaydı veya ses kaydı yapılmaz.

---

## 🗺️ İçindekiler

1. [Proje Özellikleri](#proje-özellikleri)
2. [Klasör Yapısı](#klasör-yapısı)
3. [Gereksinimler](#gereksinimler)
4. [Hızlı Başlangıç](#hızlı-başlangıç)
5. [Yapılandırma](#yapılandırma)
6. [Spotify API Kurulumu](#spotify-api-kurulumu)
7. [Genius API Kurulumu (İsteğe Bağlı)](#genius-api-kurulumu-i̇steğe-bağlı)
8. [YouTube Cookie Kurulumu](#youtube-cookie-kurulumu)
9. [Büyük Botlar için Sharding (1000+ Sunucu)](#büyük-botlar-için-sharding-1000-sunucu)
10. [Slash Komutları ve Kontroller](#slash-komutları-ve-kontroller)
11. [Dil Desteği](#dil-desteği)
12. [Dağıtım İpuçları](#dağıtım-i̇puçları)
13. [Sorun Giderme](#sorun-giderme)
14. [Gizlilik ve Yasal](#gizlilik-ve-yasal)
15. [Katkıda Bulunma](#katkıda-bulunma)

---

## Klasör Yapısı

```
discord-musicbot/
├── commands/           # Slash komut işleyicileri (play, help, search, language, ...)
├── events/             # Oynatma arayüzü için buton ve modal kontrolcüleri
├── src/                # Çekirdek servisler: MusicPlayer, MusicEmbedManager, sağlayıcılar
├── languages/          # 21 JSON dil paketi
├── database/           # Sunucu dil tercihleri için node-json-db deposu
├── config.js           # Merkezi yapılandırma + ortam değişkeni yedekleri
├── index.js            # Bot başlatma, istemci bağlantısı, ses otomatik temizleme
├── LICENSE             # MIT Lisansı
├── PRIVACY_POLICY.md   # Veri işleme detayları
└── TERMS_OF_SERVICE.md # Kabul edilebilir kullanım yönergeleri
```

---

## Gereksinimler

- **Node.js** ≥ 24+ (LTS önerilir) ve npm.
- **Git** — depoyu klonlamak için.
- **Discord uygulaması** — [Discord Geliştirici Portalı](https://discord.com/developers/applications)'nda bot kullanıcısı oluşturulmuş olmalı.
- *(İsteğe bağlı ama önerilir)* Discord ses bölgelerine kararlı bant genişliği ve düşük gecikmeyle sahip bir VPS veya hosting.

> ℹ️ `ffmpeg-static` proje ile birlikte gelir. Özel bir derleme tercih etmiyorsanız sistem genelinde FFmpeg kurmanıza **gerek yoktur**.

---

## Hızlı Başlangıç

### Windows hızlı kurulum

```powershell
.\setup.bat
# Oluşturulan .env dosyasını kimlik bilgilerinizle düzenleyin
.\start.bat
```

`setup.bat` Node.js/npm'yi doğrular, bağımlılıkları yükler ve henüz yoksa bir `.env` şablonu oluşturur. `start.bat` ortamınızın hazır olduğundan emin olup botu `npm run start` ile başlatır.

### Çapraz platform manuel adımlar

```powershell
# 1. Klonla ve gir
git clone https://github.com/umutxyp/musicbot.git discord-musicbot
cd discord-musicbot

# 2. Bağımlılıkları yükle
npm install

# 3. Gizli bilgileri yapılandır
Copy-Item .env .env.backup -ErrorAction SilentlyContinue
# .env dosyasını token, client ID, Spotify kimlik bilgileri vb. ile düzenle

# 4. Botu başlat
npm run start
# veya
node index.js
```

Slash komutları bot başladığında otomatik olarak kaydedilir. `GUILD_ID` sağlanırsa sunucu kapsamlı dağıtım saniyeler içinde gerçekleşir; global dağıtım Discord önbellek kurallarına göre bir saate kadar sürebilir.

---

## Yapılandırma

SigmaMusic hem `config.js` varsayılanlarından hem de `.env` aracılığıyla ortam değişkenlerinden okur.

### `.env` Özet Tablosu

```dotenv
DISCORD_TOKEN=bot_tokeniniz
CLIENT_ID=uygulama_id_niz
GUILD_ID=hızlı_test_için_isteğe_bağlı_sunucu_id
SPOTIFY_CLIENT_ID=spotify_client_id
SPOTIFY_CLIENT_SECRET=spotify_client_secret
GENIUS_CLIENT_ID=isteğe_bağlı_genius_client_id
GENIUS_CLIENT_SECRET=isteğe_bağlı_genius_client_secret
STATUS=🎵 SigmaMusic | /play
EMBED_COLOR=#FF6B6B
SUPPORT_SERVER=https://discord.gg/sunucu_linkiniz
WEBSITE=https://siteniz.com
COOKIES_FROM_BROWSER=chrome
COOKIES_FILE=./cookies.txt
```

### Temel Ayarlar

| Ayar | Konum | Amaç |
| --- | --- | --- |
| `discord.token` | `.env` → `config.discord.token` | Giriş ve REST kaydı için Discord bot tokeni. |
| `discord.clientId` | `.env` → `config.discord.clientId` | Slash komutlarını kaydetmek için gereken Uygulama ID'si. |
| `discord.guildId` | `.env` → `config.discord.guildId` | 1 dakikadan kısa komut dağıtımı için isteğe bağlı test sunucusu ID'si. Global kayıt için boş bırakın. |
| `bot.status` | `.env`/`config.js` | "Dinliyor..." olarak gösterilen etkinlik metni. |
| `bot.embedColor` | `.env`/`config.js` | Tüm embed'ler için hex renk kodu. |
| `spotify.clientId` ve `spotify.clientSecret` | `.env`/`config.js` | Spotify arama, çalma listesi ve albüm genişletmeyi etkinleştirir. |
| `genius.clientId` ve `genius.clientSecret` | `.env`/`config.js` | Daha yüksek hız limitleri için isteğe bağlı Genius API kimlik bilgileri. |
| `ytdl.cookiesFromBrowser` ve `ytdl.cookiesFile` | `.env`/`config.js` | YouTube cookie hatalarına karşı isteğe bağlı cookie desteği. |

> 🔐 `.env` dosyasını kaynak kontrolüne asla yüklemeyin. Hosting sağlayıcınızda dağıtım gizli bilgilerini kullanın.

---

## Spotify API Kurulumu

1. [Spotify Geliştirici Panosu](https://developer.spotify.com/dashboard/)'nu ziyaret edin, giriş yapın ve **Create an App**'e tıklayın.
2. Entegrasyonunuzu adlandırın (örn. `SigmaMusic Bot`) ve **Web API**'yi etkinleştirin.
3. **Client ID** ve **Client Secret**'ı açıklayıp kopyalayın.
4. Bir yönlendirme URI'si ekleyin (herhangi bir geçerli URL, örn. `https://localhost/callback`).
5. Her iki değeri de `.env`'nize yapıştırın (`SPOTIFY_CLIENT_ID`, `SPOTIFY_CLIENT_SECRET`).
6. Botu yeniden başlatın. Kimlik bilgileri otomatik olarak önbelleğe alınır ve yenilenir.

Bu kimlik bilgileri olmadan Spotify istekleri sıfır sonuç döndürür.

---

## Genius API Kurulumu (İsteğe Bağlı)

SigmaMusic varsayılan olarak Genius'tan sözleri çekmek için **web kazıma** kullanır — API anahtarı gerekmez! Ancak **daha yüksek hız limitleri** ve **daha hızlı yanıtlar** istiyorsanız isteğe bağlı olarak Genius API kimlik bilgilerini ekleyebilirsiniz.

### Neden Genius API Kullanmalıyım?

| API Anahtarı Olmadan | API Anahtarıyla |
| --- | --- |
| ✅ Web kazıma ile mükemmel çalışır | ✅ Daha yüksek hız limitleri |
| ✅ Kayıt gerektirmez | ✅ Daha hızlı yanıt süreleri |
| ⚠️ Yoğun kullanımda hız limitine takılabilir | ✅ Resmi API desteği |

### Kurulum Adımları

1. [Genius API İstemcileri Sayfası](https://genius.com/api-clients)'nı ziyaret edin.
2. **New API Client**'a tıklayın ve doldurun.
3. **Client ID** ve **Client Secret**'ı kopyalayıp `.env`'nize ekleyin:
   ```dotenv
   GENIUS_CLIENT_ID=genius_client_id_niz
   GENIUS_CLIENT_SECRET=genius_client_secret_niz
   ```
4. Botu yeniden başlatın.

---

## YouTube Cookie Kurulumu

YouTube zaman zaman yt-dlp'yi "Bot olmadığını doğrulamak için giriş yap" hatasıyla engelleyebilir. Bunu düzeltmek için yt-dlp'ye tarayıcı cookie'leri sağlamanız gerekir.

### Yöntem 1: Tarayıcı Cookie'leri (Önerilen)

`.env` dosyasına tarayıcınıza göre ekleyin:
```env
# Chrome kullanıcıları için
COOKIES_FROM_BROWSER=chrome

# Firefox kullanıcıları için
COOKIES_FROM_BROWSER=firefox

# Edge kullanıcıları için
COOKIES_FROM_BROWSER=edge
```

Tarayıcınızda YouTube'a giriş yaptığınızdan emin olun ve botu yeniden başlatın.

### Yöntem 2: cookies.txt Dosyası

1. Tarayıcı eklentisiyle cookie'leri dışa aktarın:
   - **Chrome/Edge:** [Get cookies.txt LOCALLY](https://chrome.google.com/webstore/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc)
   - **Firefox:** [cookies.txt](https://addons.mozilla.org/en-US/firefox/addon/cookies-txt/)

2. YouTube'da giriş yapıp cookie'leri `cookies.txt` adıyla dışa aktarın.
3. `cookies.txt` dosyasını `index.js` ile aynı klasöre koyun.
4. `.env` dosyasına ekleyin:
   ```env
   COOKIES_FILE=./cookies.txt
   ```
5. Botu yeniden başlatın.

> 🔒 `cookies.txt` dosyanızı gizli tutun ve asla paylaşmayın; YouTube oturum verilerinizi içerir.

---

## Büyük Botlar için Sharding (1000+ Sunucu)

Botunuz **1.000+ sunucuya** ulaştığında Discord, yükü birden fazla işleme dağıtmak için sharding kullanmanızı **zorunlu kılar**.

### 🚀 Sharding ile Hızlı Başlangıç

```powershell
# Sharding modunu başlat
node shard.js
```

### ⚙️ Sharding Yapılandırması

```dotenv
TOTAL_SHARDS=auto
SHARD_LIST=auto
SHARD_MODE=process
SHARD_RESPAWN=true
SHARD_SPAWN_DELAY=5500
SHARD_SPAWN_TIMEOUT=30000
```

### Kaç Shard Gerekir?

| Sunucu Sayısı | Önerilen Shard |
| --- | --- |
| < 1.000 | Sharding gerekmez (`node index.js` kullanın) |
| 1.000 - 2.000 | 2 shard |
| 2.000 - 3.000 | 3 shard |
| 5.000+ | 5+ shard |

---

## Slash Komutları ve Kontroller

| Komut | Ne Yapar |
| --- | --- |
| `/play <sorgu>` | Platform bağlantılarını veya arama anahtar kelimelerini otomatik algılar, çalma listelerini/albümleri kuyruğa ekler ve kontrol panelini başlatır. |
| `/search <anahtar kelimeler>` | YouTube eşleşmelerinin sayfalandırılmış seçim menüsünü sunar. |
| `/nowplaying` | Kuyruk durumu, tekrar/karıştır bayrakları ve ses bilgisiyle canlı embed'i tekrar gösterir. |
| `/language` | Anlık yerelleştirme için dil seçim menüsünü açar. |
| `/help` | Yerelleştirilmiş özellik turu ve destek bağlantıları. |

### Embed Üzerindeki Kontroller

- **⏸️ / ▶️ Duraklat ve Devam Et**
- **⏭️ Atla** – Kuyruktaki bir sonraki öğeye atlar.
- **⏹️ Durdur** – Kuyruğu temizler, sesi kapatır ve paneli kilitler.
- **📋 Kuyruk** – Sonraki 10 parçayı gerçek zamanlı ilerleme çubuğuyla gösterir.
- **🔀 Karıştır** – Kuyruğu rastgele sıralar (en az 2 parça gerekir).
- **🔊 Ses** – 0–100 girişine izin veren bir modal açar.
- **🔁 Döngü** – Döngü modları arasında geçiş yapar: Kapalı → Parça Tekrar → Kuyruk Tekrar.
- **🎲 Otomatik Oynatma** – Tür tabanlı otomatik oynatmayı açar/kapatır.

---

## Dil Desteği

Hazır çeviriler (ve eşleşen bayrak butonları):

**Arapça**, **Almanca**, **İngilizce**, **İspanyolca**, **Fransızca**, **Endonezce**, **İtalyanca**, **Japonca**, **Hollandaca**, **Portekizce**, **Rusça**, **Türkçe**, **Geleneksel Çince**, **Basitleştirilmiş Çince**, **Hintçe**, **Fince**, **Danca**, **Norveççe**, **Lehçe**, **Korece**, **İsveççe**

Kendi dilinizi eklemek için `languages/en.json`'u kopyalayın, metinleri çevirin ve botu yeniden başlatın.

---

## Dağıtım İpuçları

- **Test Sunucusu** – Geliştirme sırasında global yayılma gecikmesinden kaçınmak için `GUILD_ID` ayarlayın. Üretime geçmeden önce kaldırın.
- **Süreç Yöneticisi** – Botu canlı tutmak ve çökmelerde yeniden başlatmak için `pm2`, `systemd` veya Docker kullanın.
- **Kayıtlama** – Uzun vadeli izleme için stdout/stderr'i günlük dosyalarına yönlendirin.

---

## Sorun Giderme

| Belirti | Çözüm |
| --- | --- |
| Slash komutları görünmüyor | `CLIENT_ID`'nin doğru olduğundan ve botun başarıyla giriş yaptığından emin olun. |
| Spotify parçaları sonuç döndürmüyor | `SPOTIFY_CLIENT_ID`/`SECRET`'ı doğrulayın. |
| Bot katılıyor ama ses çalmıyor | Hostingde giden UDP'nin açık olduğunu ve ses kanalı izinlerinin **Bağlan** ve **Konuş**'a izin verdiğini onaylayın. |
| Butonlar şarkı ortasında çalışmıyor | Etkileşimler Discord TTL'si dolduktan sonra sona erer. Paneli yenilemek için `/play` komutunu tekrar kullanın. |
| **YouTube bot algılama hatası** | **YouTube, cookie aracılığıyla bot doğrulaması gerektirir. Detaylı talimatlar için [YouTube Cookie Kurulumu](#youtube-cookie-kurulumu) bölümüne bakın.** |

---

## Gizlilik ve Yasal

- **Gizlilik Politikası** – Sakladığımız verilerin tam olarak neler olduğu (sunucu ID'si + dil tercihi) ve silme talebinde bulunma yöntemi.
- **Hizmet Şartları** – Kabul edilebilir kullanım, sorumluluk sınırları ve iletişim bilgileri.
- **Lisans** – MIT. Özel veya ticari olarak kullanın — sadece bildirimi saklayın.

---

## Katkıda Bulunma

1. Depoyu forklayın ve bir özellik dalı oluşturun.
2. Bağımlılıkları yüklemek için `npm install` çalıştırın.
3. Özellikler ekleyin veya iyileştirin (çeviri paketleri, arayüz değişiklikleri, yeni sağlayıcılar).
4. Açık bir açıklama ve ilgili ekran görüntüleri/konsol çıktılarıyla bir pull request açın.

---

Keyifli dinlemeler, sunucuları sallamaya devam! 🎧
