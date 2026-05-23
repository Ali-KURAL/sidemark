# Sidemark — Yayın Rehberi

## Hızlı Bakış

| Adım | Durum |
|------|-------|
| Backend (Railway) | ✅ Canlı |
| Privacy Policy | ✅ Yayında |
| Admin Paneli | ✅ Hazır |
| Extension kodu | ✅ GitHub'da |
| Chrome Web Store kaydı | ⬜ Yapılmadı |
| Store görselleri | ⬜ Hazırlanmadı |
| Chrome Web Store yayını | ⬜ Yapılmadı |

---

## 1. Railway Ortam Değişkenleri

`sidemark-backend` → Variables kısmında şunların set edildiğinden emin ol:

| Değişken | Açıklama |
|----------|----------|
| `API_KEY` | Extension'ın backend'e erişim anahtarı |
| `DATABASE_URL` | `${{Postgres.DATABASE_URL}}` (PostgreSQL bağlantısı) |
| `ADMIN_USERNAME` | Admin paneli kullanıcı adı |
| `ADMIN_PASSWORD` | Admin paneli şifresi |

**Admin paneli:** `https://sidemark-backend-production.up.railway.app/pages/admin.html`

---

## 2. manifest.json Güncellemesi

`extension/manifest.json` dosyasına şunu ekle:

```json
"homepage_url": "https://github.com/Ali-KURAL/sidemark-extension"
```

Ekledikten sonra extension'ı commit'le:

```bash
cd extension
git add manifest.json
git commit -m "Add homepage_url to manifest"
git push
```

---

## 3. Görselleri Hazırla

Chrome Web Store için gereken görseller:

| Görsel | Boyut | Nasıl? |
|--------|-------|--------|
| **Screenshot** (zorunlu, 1-5 adet) | 1280x800 veya 640x400 | Extension açıkken ekran görüntüsü → Canva/Photoshop'ta boyutlandır |
| **Promo Tile** (isteğe bağlı) | 440x280 | Logo + kısa slogan |

**Screenshot önerisi:** Popüler bir sayfa (örn. bir YouTube videosu veya haber) açıkken extension popup'ını aç, birkaç yorum varken ekran görüntüsü al.

---

## 4. Chrome Web Store'a Kayıt

1. [chromewebstore.google.com/devconsole](https://chromewebstore.google.com/devconsole) adresine git
2. Google hesabınla giriş yap
3. **$5 geliştirici kayıt ücreti** öde (tek seferlik, kredi kartı)

---

## 5. Extension ZIP'i Oluştur

`extension/` klasörünün **içindeki** dosyaları ZIP'le (klasörün kendisini değil):

```
manifest.json
popup.html
popup.js
popup.css
i18n.js
icons/
```

Windows'ta: `extension/` klasörüne gir → tüm dosyaları seç → sağ tıkla → Sıkıştır.

---

## 6. Store'a Yükle

1. Dev Console'da **"New Item"** → ZIP dosyasını yükle
2. Aşağıdaki formu doldur:

### Store Listing

**Name:**
```
Sidemark
```

**Summary** (132 karakter maks):
```
Leave and read comments on any webpage. Like Google Reviews but for every URL.
```

**Description:**
```
Sidemark lets you leave and read comments on any webpage — news articles, YouTube videos, e-commerce products, blog posts, and more.

How it works:
1. Install Sidemark
2. Visit any webpage
3. Click the extension icon
4. Read comments from other users, or leave your own

Features:
- Works on every URL
- Threaded replies (like YouTube comments)
- Like system — most liked comments rise to the top
- Pagination for pages with many comments
- Delete your own comments anytime
- 6 languages: English, Turkish, Spanish, Chinese, Hindi, Arabic

Comments are stored on a shared server — everyone visiting the same URL sees the same comments.

Privacy: We collect only your chosen username and comment text. No email, no account required. Full privacy policy: https://sidemark-backend-production.up.railway.app/pages/privacy.html
```

**Category:** Productivity  
**Language:** English

### Privacy

- **Privacy Policy URL:**
  ```
  https://sidemark-backend-production.up.railway.app/pages/privacy.html
  ```
- "Does your extension collect user data?" → **Yes**
  - User activity → comment text you submit

### Permissions Justification

Review sırasında sorulursa:

| Permission | Açıklama (İngilizce yaz) |
|------------|--------------------------|
| `activeTab` | To read the current tab's URL in order to fetch and display comments for that page |
| `storage` | To save the user's chosen username and liked comment IDs locally on their device |
| Host permission (Railway URL) | To communicate with the backend API for reading and posting comments |

---

## 7. İnceleme Süreci

- Gönderim sonrası genellikle **1–3 iş günü** bekle
- Onaylanırsa e-posta gelir, extension store'da yayına girer
- Reddedilirse red nedeni e-postayla bildirilir — genellikle permission açıklaması veya privacy policy eksikliğidir, düzeltip tekrar gönderirsin

---

## 8. Yayın Sonrası

### Extension ID'yi al
Store'da yayına girince extension'ın bir ID'si olur (örn. `abcdefghijklmnopqrstuvwxyzabcdef`).
Bu ID, ileride **Google OAuth** eklemek için gerekli.

### Güncelleme göndermek
```bash
cd extension
# Değişiklikleri yap
# manifest.json'da "version" numarasını artır: "1.0.0" → "1.0.1"
git add .
git commit -m "v1.0.1: ..."
git push
# Dev Console → extension → "Upload new package" → yeni ZIP yükle
```

### Versiyon numarası kuralı
- `1.0.x` → küçük düzeltmeler
- `1.x.0` → yeni özellik
- `x.0.0` → büyük değişiklik

---

## 9. Sıradaki Özellikler (Yayın Sonrası)

1. **Google OAuth** — Yayın sonrası extension ID alınınca eklenecek
   - Google Cloud Console → OAuth client ID (Chrome App türü)
   - Extension ID'yi kaydet
   - `manifest.json`'a `identity` permission + `oauth2` section ekle
   - `chrome.identity.getAuthToken` ile token al

2. **Yorum bildirimleri** — Yanıt gelince kullanıcıya bildirim

3. **Freemium** — Google OAuth sonrası, premium özellikler için ödeme sistemi

---

## Linkler

| | URL |
|-|-----|
| Backend repo | https://github.com/Ali-KURAL/sidemark-backend |
| Extension repo | https://github.com/Ali-KURAL/sidemark-extension |
| Backend canlı | https://sidemark-backend-production.up.railway.app |
| Privacy Policy | https://sidemark-backend-production.up.railway.app/pages/privacy.html |
| Admin Panel | https://sidemark-backend-production.up.railway.app/pages/admin.html |
| Railway Dashboard | https://railway.app |
| Chrome Dev Console | https://chromewebstore.google.com/devconsole |
