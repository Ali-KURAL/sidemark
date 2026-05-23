# Sidemark — Premium Strateji

## Temel Prensip

Free kullanıcılar kısıtlanmış hissetmemeli — premium, ekstra güç vermeli.
Like, yorum yazma, yanıtlama gibi core özellikler her zaman ücretsiz kalır.

---

## Free vs Premium

| Özellik | Free | Premium |
|---------|------|---------|
| Yorum okuma | ✅ | ✅ |
| Yorum yazma | ✅ | ✅ |
| Yanıt verme | ✅ | ✅ |
| Beğeni | ✅ | ✅ |
| Kendi yorumunu silme | ✅ | ✅ |
| **Verified rozet** ✓ | ❌ | ✅ |
| **Markdown** (bold, link, italic) | ❌ | ✅ |
| **Kod bloğu** | ❌ | ✅ |
| **Özel avatar rengi** | ❌ | ✅ |
| **Yorum geçmişi** | ❌ | ✅ |

---

## Özellik Detayları

### Verified Rozet ✓
Kullanıcı adının yanında küçük mavi tik. Google OAuth ile giriş yapan
ve premium olan kullanıcılara verilir. Spam hesaplardan ayırt etmeyi
kolaylaştırır, aynı zamanda sosyal statü sağlar.

### Markdown Desteği
Premium kullanıcılar yorumlarında şunları kullanabilir:
- `**bold**` → **bold**
- `*italic*` → *italic*
- `[link](url)` → tıklanabilir link
- Backtick ile `` `inline kod` ``

Free kullanıcı aynı metni yazarsa düz metin olarak görünür.

### Kod Bloğu
Teknik sayfalarda (GitHub, Stack Overflow, dökümantasyon) faydalı.
Üç backtick ile yazılır:

```
function hello() {
  return "world";
}
```

Syntax highlight eklenebilir (Prism.js gibi bir kütüphaneyle).

### Özel Avatar Rengi
Şu an avatar rengi kullanıcı adından otomatik hesaplanıyor.
Premium kullanıcılar renk paletinden istediğini seçebilir.
Küçük ama kişiselleştirme hissi güçlü.

### Yorum Geçmişi
"Benim Yorumlarım" sayfası — kullanıcının hangi sayfalara
yorum bıraktığını toplu gösterir. Bunun için Google OAuth zorunlu
(anonim kullanıcının tüm yorumlarını bulmak mümkün değil).

---

## Teknik Ön Koşul

**Tüm premium özellikler Google OAuth'a bağlı.**
OAuth olmadan kimin premium olduğunu doğrulamanın yolu yok.

Sıra şu:
```
Chrome Web Store yayını → Extension ID al → Google OAuth ekle → Premium ekle
```

---

## Fiyatlandırma Önerisi

| Plan | Fiyat | Hedef |
|------|-------|-------|
| Free | $0 | Herkes |
| Premium | $3/ay veya $25/yıl | Güçlü kullanıcılar |

Tek seferlik ödeme de düşünülebilir ($9–12 lifetime).
Abonelik yerine lifetime tercih eden kullanıcı segmenti var.

---

## Ödeme Altyapısı

**LemonSqueezy** önerilir (Stripe'a göre kurulumu çok daha kolay,
vergi yönetimi otomatik, Türkiye'den sorunsuz çalışır).

Alternatif: **Stripe** (daha yaygın ama kurulumu daha karmaşık).

---

## Spam Koruması Notu

Like'ı premium'a kilitlemek yanlış — engagement kalabalıkla çalışır.
Mevcut korumalar yeterli:
- IP bazlı like koruması ✅
- Rate limiting ✅
- Google OAuth (yakında) → hesaplı kullanıcılar spam yapmaz
