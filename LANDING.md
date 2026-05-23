# Sidemark — Her Sayfaya Yorum Bırak

> Google Yorumları gibi, ama her web sayfası için.

---

## Nedir?

Sidemark, ziyaret ettiğin her web sayfasına yorum bırakmanı sağlayan bir Chrome eklentisidir. Netflix'te bir dizi, haber sitesinde bir makale, YouTube'da bir video — nerede olursan ol, aynı sayfayı açan diğer kullanıcıların yorumlarını görebilir ve kendi yorumunu ekleyebilirsin.

---

## Nasıl Çalışır?

1. Chrome'a Sidemark eklentisini yükle
2. Herhangi bir sayfaya git
3. Eklenti ikonuna tıkla
4. O sayfadaki yorumları oku, kendi yorumunu yaz

Yorumlar merkezi bir sunucuda saklanır. Aynı sayfayı açan herkes aynı yorumları görür.

---

## Özellikler

- **Evrensel** — Her URL desteklenir: haber, video, e-ticaret, blog…
- **Anlık** — Yorumlar gerçek zamanlı olarak diğer kullanıcılara görünür
- **Yanıtlar** — YouTube tarzı iç içe yanıt sistemi
- **Beğeniler** — En beğenilen yorumlar öne çıkar, like sayısına göre sıralanır
- **Sayfalama** — Yorumlar sayfa sayfa yüklenir, "Daha fazla göster" ile devam edilir
- **Akıllı URL tanıma** — Aynı içeriğin farklı URL varyantları tek sayfada birleşir
- **Google ile giriş** — Güvenli kimlik doğrulama (yakında)
- **Kendi yorumunu sil** — Yazdığın yorumları istediğinde kaldır
- **Admin moderasyon paneli** — Spam ve uygunsuz yorumları yönet

---

## Teknik Altyapı

| Bileşen | Teknoloji |
|---|---|
| Chrome Eklentisi | Manifest V3, Vanilla JS |
| Backend API | Node.js + Express |
| Veritabanı | PostgreSQL |
| Hosting | Railway |
| Kimlik Doğrulama | Google OAuth (chrome.identity) |

---

## Kurulum (Geliştirici)

### Backend

```bash
cd backend
npm install
# Local geliştirme: DATABASE_URL olmadan JSON dosyası kullanır
npm run dev
```

### Extension

1. Chrome'da `chrome://extensions/` aç
2. **Geliştirici modu**'nu aç
3. **Paketlenmemiş öğe yükle** → `extension/` klasörünü seç

### Ortam Değişkenleri

```env
PORT=3000
API_KEY=guclu-bir-sifre
DATABASE_URL=postgresql://...   # Railway'de otomatik set edilir
```

---

## Google OAuth Kurulumu (Production)

Google girişini aktif etmek için:

1. [Google Cloud Console](https://console.cloud.google.com) → Yeni proje
2. **APIs & Services** → **Credentials** → **Create Credentials** → **OAuth client ID**
3. Uygulama türü: **Chrome App**
4. Extension ID'ni gir (`chrome://extensions/` sayfasından)
5. Oluşturulan `client_id`'yi `extension/manifest.json` dosyasındaki `oauth2.client_id` alanına yaz
6. Chrome Web Store'a yayınla

---

## Yol Haritası

- [x] Temel yorum sistemi
- [x] Yanıtlar (1 seviye)
- [x] Beğeni sistemi
- [x] URL normalizasyonu
- [x] Railway deploy
- [x] API key koruması + Rate limiting
- [x] Kendi yorumunu silme
- [x] Sayfalama (pagination)
- [x] Admin moderasyon paneli
- [ ] Google OAuth girişi
- [ ] Chrome Web Store yayını
- [ ] Yorum bildirimleri

---

## İletişim

Proje hakkında sorularınız için: [GitHub Issues](https://github.com/Ali-KURAL/sidemark-backend/issues)
