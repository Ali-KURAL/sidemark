# Sidemark — Marketing Playbook

> Solo dev, $20 cap, 6+ ay horizon. Viral/sosyal ürün — network effect kritik.

---

## Konumlandırma

**One-liner (EN):** *Comments on any webpage. Like Genius / Disqus, but for every URL.*

**One-liner (TR):** *Her web sayfasına yorum bırak ve oku. Hesap gerekmez.*

**Differentiator:** Her URL'de çalışır (site entegrasyonu yok), hesap yok, 6 dil.

### Audience katmanları
| Tier | Kim | Mesaj |
|---|---|---|
| 1 (early) | Indie devs, Reddit/HN power users, internet enthusiasts | "Hesap istemeyen, her sayfada çalışan Disqus alternatifi" |
| 2 (mainstream) | Haber/YouTube yorumlayan genel kitle | "Bu sayfa hakkında başkaları ne diyor?" |
| 3 (B2B, long-term) | Yayıncılar, yorum sistemi arayan small siteler | "Lightweight, gömme gerektirmeyen yorum sistemi" |

---

## Pre-Launch Checklist

- [ ] Chrome Web Store listing tamam + 5 screenshot
- [ ] 1280×800 screenshots: ana popup, popüler sayfada gerçek yorumlar, threaded reply, RTL/Arabic, multi-language
- [ ] 440×280 promo tile (Canva free yeterli)
- [ ] 30-60 sn demo video (Windows Game Bar / Loom free tier)
- [ ] Landing page: opsiyonel — `carrd.co` free veya GitHub Pages
- [ ] Twitter hesabı + bio + extension link
- [ ] 5 adet build-in-public tweet hazır (launch sırasında zaman kazanmak için)
- [ ] One-liner 3 dilde hazır (TR/EN/ES min)

---

## Launch Sequence

### Hafta −1 (hazırlık)
| Gün | Aksiyon |
|---|---|
| Pzt | Chrome Web Store submit (1-3 gün review) |
| Sal | Product Hunt "Upcoming" sayfası oluştur (4 hafta önce çizelgeleyebilirsin) |
| Çar-Cum | Screenshot + demo video |
| Hafta sonu | Show HN draftı + 3 farklı Reddit post taslağı |

### Hafta 0 (Launch Week)

**Pazartesi — Soft launch**
- Twitter: "Sidemark Chrome Store'da" + screenshot
- 5-10 indie dev arkadaşına DM
- Hedef: ilk 20-50 install (review seed'i için)

**Salı — Product Hunt + Show HN (kritik gün)**
- 00:01 PST: Product Hunt go-live (hunter önceden ayarla)
- İlk 4 saat online — her yoruma yanıt
- 09:00 PT: Show HN post
- İlk yorum SEN: build motivation + dürüst limitations
- Hedef: 200+ upvote PH, top 10 daily HN

**Çarşamba — Reddit wave 1**
- `r/chrome_extensions` (15K, doğrudan fit, OK to share)
- `r/SideProject` (200K, founder topluluğu)
- Post format: "X için Y yaptım, böyle çalışıyor"
- 24 saat her yoruma yanıt

**Perşembe — Reddit wave 2 (niche)**
- `r/InternetIsBeautiful` (19M, viral potansiyel, sıkı kurallar — oku)
- `r/Genius` (annotation enthusiasts)
- En az 48 saat farklı sub'lar arasında

**Cuma — Recap + retro**
- Twitter thread: launch week stats + ne işe yaradı
- PH yorum güncelle (traction iyiyse)
- 3-5 newsletter operatörüne e-posta (growth iyiyse)

### Hafta 1-2 (Post-launch)
- Günlük: Chrome Store review yanıtla, GitHub issue çöz
- Twitter: haftada 2-3x — feature, bug fix, mini milestone
- Reddit: 3-4 günde bir farklı sub, asla tekrar etme
- Testimonial topla (landing page için)

---

## Channel Playbooks

### Chrome Web Store SEO

**Title:** `Sidemark — Comment on Any Webpage`

**Short description (132 char max):**
> Leave and read comments on any webpage. Like Google Reviews but for every URL. Threaded replies, 6 languages, free.

**Screenshot sırası:**
1. Popüler haber makalesinde gerçek yorumlarla açık popup
2. Threaded reply view
3. RTL / Arabic arayüz (uluslararası mesaj)
4. URL normalization açıklaması (utm_*, fbclid temizleme)
5. "No account required" privacy feature box

**Update kadansı:** 2-3 haftada bir screenshot/description güncelle — store algoritması "active maintenance" sinyali sever.

---

### Product Hunt

**Tagline aday:** *Like Genius but for every webpage*

**İlk yorum template:**
> Hi PH! Sidemark'i [genuine pain point] yüzünden yaptım. Herhangi bir URL'e yorum bırakabilirsiniz — haber, YouTube, e-ticaret. Threaded replies, hesap gerekmez, 6 dil.
>
> [N hafta] solo. En zor kısmı [interesting technical detail — örn. CORS canvas issue].
>
> Demo: [link]. Ücretsiz (Premium tier yolda).
>
> AMA!

**Hunter:** Kendinden büyük bir indie dev bul. Twitter DM yeterli — most are responsive.

---

### Hacker News Show HN

**Title:** `Show HN: Sidemark – Comment on any webpage`

**Submit zamanı:** Sal/Çar/Per 09:00 PT veya Paz 20:00 PT.

**İlk yorum (sen):**
- WHY (motivation)
- HOW (1-2 technical highlight)
- LIMITATIONS (dürüst ol — HN bunu sever)

**Karşı argümanlara yanıt:** technical depth, savunmasız. HN marketing dilinden nefret eder; gerçek dev sesi kazanır.

---

### Reddit — sıkı kurallar

**Yapılacaklar:**
- Her sub'ın kuralını oku (bazıları sadece Salı kabul eder)
- Value-first açılış ("Y problemini çözmek için X yaptım")
- 24 saat her yorumu yanıtla
- Diğer aktif yorumlarına link bırak (otantiklik)

**Yapılmayacaklar:**
- Aynı text farklı sub'lara (shadowban riski)
- Marketing dili ("revolutionary", "game-changing")
- Negatif yoruma savunmacı yanıt
- Düşük trafikli saatlerde post

**Best sub'lar (etki sırası):**
1. r/chrome_extensions (direct fit)
2. r/SideProject (founder topluluğu)
3. r/InternetIsBeautiful (viral potansiyel, kuralları çok sıkı)
4. r/Genius (annotation enthusiasts, küçük ama angaje)
5. r/news / r/worldnews (büyük ama self-promo'ya şüpheli)

---

### Twitter / X — long game

- Günlük build-in-public: install sayısı, MRR, mini feature
- Engage: `@levelsio`, `@nathanbarry`, `@arvidkahl`, `@yongfook`
- Thread format: "I built X. Here's what I learned." (5-7 tweet)
- Reply guy stratejisi: büyük indie account tweet'lerinin altında ilk yararlı reply

---

## Long-term Content Calendar

**Haftalık:**
- 1 tweet thread (build-in-public update)
- 1 blog post (SEO targets aşağıda)
- 1 küçük product update (public changelog)

**Aylık:**
- 1 YouTube/Loom video (tutorial veya comparison)
- 1 Reddit post farklı sub'da
- 1 newsletter operator outreach

**Çeyreklik:**
- 1 milestone announcement (1K user, vb.)
- Büyük update varsa Product Hunt re-launch

**SEO target keywords (blog için):**
- "comment on every webpage"
- "Disqus alternative"
- "annotation tools chrome"
- "Genius alternative 2026"
- "comment system for any URL"

---

## $20 Budget Tahsisi

**Önerilen (asset focus):**
| Kalem | Tutar | Etki |
|---|---|---|
| Canva Pro 1 ay | $14.99 | Profesyonel screenshot + promo tile (kalıcı conversion artışı) |
| Domain (sidemark.app) | $5 | Twitter bio + landing page için autoritu |
| **Toplam** | **$20** | |

Ücretli reklam **almayın**. $20 ile anlamlı Reddit/Twitter campaign mümkün değil — asset'e yatırım organic conversion'u kalıcı artırır.

**Alternatif (asset zaten hazırsa):**
- $20 Reddit ads test, 4 gün × $5/gün, r/chrome_extensions targeting

---

## Metrics to Track

**Hafta 1:**
- Chrome Store installs (günlük)
- Product Hunt upvotes
- HN points
- Reddit upvotes/comments

**Ay 1+:**
- Weekly Active Users (backend logları + flash count'tan tahmin)
- Yorum volume (DB'den ölçülür)
- Chrome Store rating + review count
- GitHub stars (vanity ama B2B credibility)

**Real signals:**
- Repeat usage (aynı user 7+ gün)
- Organik mention (sen aramadan Reddit/Twitter'da geçti mi)
- Newsletter mentions

---

## Anti-Patterns (yapmayın)

- ❌ Sahte review satın alma → Google tespit eder, banlar
- ❌ Aynı Reddit metni 5 sub'a → shadowban
- ❌ Kurumsal dil ("revolutionary", "next-gen") → indie/personal kazanır
- ❌ Cuma launch → hafta sonu trafiği düşük
- ❌ Negatif feedback'i ignore → yanıt ver, fix et, fix'i announce et
- ❌ Premium gate'i çok erken → 1K+ free user olmadan paid çevirme

---

## 6-Ay Roadmap (memory'den: sürdürülebilir gelir hedefi)

| Ay | Odak | KPI |
|---|---|---|
| 1-2 | Launch + organic growth | 1K-5K install, 100+ comments/day |
| 3-4 | Content marketing + SEO base | 10K install, blog organic traffic |
| 5-6 | Premium tier launch + feedback iterate | İlk $100 MRR |
| 6+ | Paid acquisition (Premium gelir ile finanse edildiğinde) | $500-1K MRR hedef |

---

## Hızlı Referans Linkler

- [Chrome Web Store dev console](https://chromewebstore.google.com/devconsole)
- [Product Hunt](https://producthunt.com)
- [Hacker News submit](https://news.ycombinator.com/submit)
- [Carrd (free landing)](https://carrd.co)
- Time zones: PT = UTC-7 (DST), Salı 00:01 PT = Salı 10:01 İstanbul
