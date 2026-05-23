# Sidemark

> Google Yorumları gibi, ama her web sayfası için.

Sidemark, ziyaret ettiğin her web sayfasına yorum bırakmana ve diğer kullanıcıların yorumlarını okumana olanak tanıyan bir Chrome eklentisidir.

---

## Repolar

| | Repo |
|-|------|
| Backend (Node.js + Express + PostgreSQL) | [sidemark-backend](https://github.com/Ali-KURAL/sidemark-backend) |
| Extension (Chrome MV3) | [sidemark-extension](https://github.com/Ali-KURAL/sidemark-extension) |

---

## Özellikler

- Her URL'de çalışır — haber, video, e-ticaret, blog…
- Threaded yanıt sistemi
- Like sayısına göre sıralama
- Pagination
- 6 dil: Türkçe, İngilizce, İspanyolca, Çince, Hintçe, Arapça
- Admin moderasyon paneli
- Kendi yorumunu sil (delete token ile korumalı)
- IP bazlı like koruması

---

## Proje Yapısı

```
sidemark/
├── backend/      # Node.js + Express REST API  (submodule)
├── extension/    # Chrome Extension MV3        (submodule)
├── CLAUDE.md     # Geliştirici notları
├── LANDING.md    # Proje tanımı
└── PUBLISH.md    # Chrome Web Store yayın rehberi
```

---

## Kurulum

```bash
git clone --recurse-submodules https://github.com/Ali-KURAL/sidemark
```

### Backend

```bash
cd backend
npm install
npm run dev
```

Ortam değişkenleri için `backend/.env.example` dosyasına bak.

### Extension

1. `chrome://extensions/` → Geliştirici modu aç
2. "Paketlenmemiş öğe yükle" → `extension/` klasörünü seç

---

## Canlı

- **Backend:** https://sidemark-backend-production.up.railway.app
- **Privacy Policy:** https://sidemark-backend-production.up.railway.app/pages/privacy.html

---

## Yol Haritası

- [x] Temel yorum sistemi
- [x] Yanıtlar
- [x] Beğeni sistemi
- [x] URL normalizasyonu
- [x] Railway deploy + PostgreSQL
- [x] API key koruması + Rate limiting
- [x] Kendi yorumunu silme (delete token)
- [x] IP bazlı like koruması
- [x] UUID comment ID'leri
- [x] Sayfalama (pagination)
- [x] Like sayısına göre sıralama
- [x] Admin moderasyon paneli
- [x] Gizlilik politikası sayfası
- [ ] Chrome Web Store yayını
- [ ] Google OAuth girişi
- [ ] Yorum bildirimleri
