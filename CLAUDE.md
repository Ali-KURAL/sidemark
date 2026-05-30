# Sidemark — CLAUDE.md

## Proje Nedir
Her web sayfasına yorum bırakılmasını sağlayan Chrome eklentisi. Google Reviews gibi ama herhangi bir URL için. Kullanıcılar aynı sayfayı açtığında birbirlerinin yorumlarını görebilir.

## Klasör Yapısı
```
sidemark/
├── backend/          # Node.js + Express REST API
│   ├── server.js     # Giriş noktası, middleware, rate limiting, API key auth
│   ├── storage.js    # Veritabanı işlemleri (PostgreSQL veya JSON dosyası)
│   ├── routes/
│   │   └── comments.js  # GET, POST, DELETE /api/comments + like/unlike
│   └── .env.example
├── extension/        # Chrome Extension (Manifest V3)
│   ├── manifest.json
│   ├── popup.html
│   ├── popup.js      # Tüm extension mantığı
│   ├── popup.css
│   ├── i18n.js       # Çoklu dil desteği (tr/en/es/zh/hi/ar)
│   └── icons/
├── LANDING.md        # Demo/tanıtım belgesi
└── CLAUDE.md         # Bu dosya
```

## Backend

### Çalıştırma
```bash
cd backend
npm install
npm run dev      # nodemon ile (local)
npm start        # production
```

### Ortam Değişkenleri
- `PORT` — Varsayılan: 3000
- `API_KEY` — Zorunlu (production'da). Set edilmezse API key kontrolü atlanır (local dev kolaylığı)
- `DATABASE_URL` — Set edilirse PostgreSQL kullanır, yoksa `comments.json` dosyasına yazar

### API Endpoints
| Method | Path | Açıklama |
|--------|------|----------|
| GET | `/health` | Backend sağlık kontrolü (API key gerektirmez) |
| GET | `/api/comments?url=` | URL'e ait yorumları getir |
| POST | `/api/comments` | Yorum ekle `{ url, username, text, parentId? }` |
| POST | `/api/comments/:id/like` | Beğen |
| POST | `/api/comments/:id/unlike` | Beğeniyi geri al |
| DELETE | `/api/comments/:id` | Yorumu sil (yanıtlarıyla birlikte) |

### Güvenlik
- Her endpoint `x-api-key` header kontrolü yapar (local'de atlanır)
- Rate limiting: okuma 200 req/15dk, yazma 30 req/15dk
- Input validation: username max 50, text max 1000 karakter
- XSS koruması: backend'e gelen veriler extension'da `escapeHtml()` ile render edilir

### Storage Mantığı
`storage.js` dual-mode çalışır:
- `DATABASE_URL` set → PostgreSQL (Railway production)
- `DATABASE_URL` yok → `comments.json` dosyası (local development)

## Extension

### Chrome'a Yükleme
1. `chrome://extensions/` aç
2. "Geliştirici modu" aç
3. "Paketlenmemiş öğe yükle" → `extension/` klasörünü seç
4. Değişiklikten sonra ⟳ ile yenile

### Önemli Dosyalar

**`popup.js`** — Tüm mantık burada:
- `normalizeUrl()` — URL'den gürültü parametrelerini temizler (`utm_*`, `fbclid` vb.), içeriğe özgü parametreleri korur (`v=` YouTube için)
- `myCommentIds` — `chrome.storage.local`'de saklanır, kullanıcının kendi yorumlarını takip eder (sil butonu için)
- `likedIds` — `chrome.storage.local`'de saklanır, çift beğeniyi önler
- Like optimistic update: önce UI'ı günceller, sonra API çağrısı yapar, hata olursa geri alır
- Form başlangıçta kapalıdır, "Yorum Ekle" butonuna basınca açılır

**`i18n.js`** — Dil desteği:
- Desteklenen diller: `tr`, `en`, `es`, `zh`, `hi`, `ar`
- Dil `navigator.language` ile otomatik algılanır
- `t('key')` fonksiyonu ile string çekilir
- Arapça için RTL desteği (`body.rtl` class'ı)

**`manifest.json`**:
- `host_permissions` içinde Railway URL'i ve localhost var
- `storage` ve `activeTab` permission'ları gerekli

## Deployment

### Railway (Production)
- Backend: `https://sidemark-backend-production.up.railway.app`
- GitHub push → Railway otomatik deploy eder
- Railway Variables: `API_KEY` set edilmeli
- PostgreSQL: Railway'in eklediği `DATABASE_URL` otomatik inject edilir

### GitHub
- Repo: `https://github.com/Ali-KURAL/sidemark-backend` (private)
- Sadece `backend/` klasörü GitHub'da, `extension/` local'de

## Google OAuth Girişi (Aktif)
Yorum yazmak için Google ile giriş **zorunlu**. Beğeni girişsiz çalışır.

- **Extension ID:** `llcgcpoakoghnafgcjcicmeciilcoodd`
- **OAuth Client ID:** `444197345778-5b22mon4srme9pvf4sg34dg39q1mvlhr.apps.googleusercontent.com` (`manifest.json` → `oauth2.client_id`)
- **Google Cloud projesi:** "Sidemark" (External consent screen, Chrome Extension client)
- Akış: `chrome.identity.getAuthToken` → access token → backend `userinfo` ile doğrular → `sub`=google_id, `name`=username saklanır
- **Güvenlik:** Username client'tan değil doğrulanmış Google profilinden alınır (taklit engelli). Backend token'sız POST'u 401 ile reddeder.
- **Token yenileme:** Her gönderimde `getAuthToken({interactive:false})` ile taze token alınır, 401'de cache temizlenip retry edilir.
- ⚠️ Google login **sadece store sürümünde** çalışır — local extension ID farklı olduğu için OAuth reddeder.

## Ertelenmiş Özellikler
- **Yorum bildirimleri** — Yanıt gelince kullanıcıya bildirim
- **Freemium** — Premium özellikler için ödeme sistemi

## Dikkat Edilecekler
- Backend değişikliği sonrası Railway deploy beklenmeli (~1-2 dk)
- Extension değişikliği sonrası `chrome://extensions/` sayfasından yenilenmeli
- Local'de `API_KEY` env var set edilmezse API key kontrolü çalışmaz (bu bilerek yapıldı)
- `comments.json` `.gitignore`'da — commit'lenmiyor
- `node_modules/` `.gitignore`'da — commit'lenmiyor
