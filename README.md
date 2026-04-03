# Ai-la — WordPress AI Admin Assistant

Ai-la, WordPress yönetim paneline entegre olan bir AI destekli asistan eklentisidir. Kullanıcıların doğal dilde sorduğu sorulara cevap verir, doğru admin sayfasına yönlendirir, adım adım rehberlik eder ve eklentiler hakkında detaylı bilgi sunar.

---

## Mevcut Durum (v2.4.8)

### Ne Yapıyor?
- Sağ altta sabit, küçük bir chat paneli olarak çalışır
- Kullanıcı soru yazar → Groq AI (Llama 3.3 70B) cevap verir
- Groq key girilmemişse 200+ keyword route ile çalışır
- Sayfaya gidince popup otomatik açılır, adım adım yönlendirme yapar
- Sohbet geçmişi localStorage'da saklanır
- Admin paneli + ön yüz + önizleme ekranında çalışır (sadece admin kullanıcılara görünür)

### Teknik Yapı
```
Kullanıcı → Chat UI → AJAX → PHP → Groq AI / Keyword Fallback → Cevap
```

**Akıl katmanları (öncelik sırasıyla):**
1. `info_routes` — Ai-la kendi ayarları, selamlama, sohbet
2. `$routes` — 200+ WordPress/eklenti yönlendirmesi
3. `smart_fallback` — kategori tahmini ile alternatif öneriler
4. Groq AI — serbest soru/cevap (key girilmişse)

---

## Özellikler

**Chat Deneyimi**
- Sağ altta sabit panel (400x600px), overlay yok — sayfa görünür kalır
- Minimize butonu — küçük launcher'a dönüşür
- Sohbet geçmişi — sayfa değişince kaybolmaz
- Sayfaya git → popup otomatik açılır, adım adım yönlendirme
- Geçmişi sil butonu (onay ile)
- Mobil uyumlu — alttan tam ekran açılır

**AI & Bilgi**
- Groq AI (Llama 3.3 70B) entegrasyonu
- Sayfa bağlamı — hangi sayfada olduğunu biliyor
- Sohbet soruları — "nasılsın", "şimdi ne yapacağım" gibi sorulara doğal cevap
- Groq key yoksa akıllı fallback + key önerisi

**Kapsanan Konular**
- WordPress core (50+ ayar sayfası)
- WooCommerce (sipariş, ürün, kargo, ödeme, stok, e-posta, abonelik)
- Elementor + 7 eklenti paketi (Royal, Essential, Happy, Premium, JetElements, Unlimited, Piotnet)
- Yoast SEO, Rank Math
- Cache eklentileri (WP Rocket, LiteSpeed, W3TC, WP Super Cache, Autoptimize, Swift)
- Çeviri (WPML, Loco Translate, Polylang, TranslatePress, Weglot)
- Güvenlik (Wordfence, brute force, 2FA, dosya izinleri, hack senaryoları)
- Hata kodları (404, 500, 403, SSL, memory limit, kritik hata, login loop)
- Hosting (cPanel, FTP, PHP ayarları, domain, SSL, site taşıma)
- LMS (LearnDash, LifterLMS, Tutor LMS, Sensei)
- Rezervasyon (Amelia, Bookly)
- Marketplace (Dokan, WCFM)
- Affiliate (AffiliateWP, Pretty Links, ThirstyAffiliates)
- E-posta (WP Mail SMTP, Mailchimp, FluentCRM, MailPoet)
- Galeri (Envira, FooGallery, Modula)
- Etkinlik (The Events Calendar, Event Tickets)
- Harita (WP Google Maps, Leaflet)
- Sosyal giriş (Nextend Social Login)
- Arama (SearchWP, Relevanssi)
- Geliştirici araçları (Query Monitor, WP-Optimize, Broken Link Checker)
- GDPR/KVKK (CookieYes, gizlilik politikası)
- Genel WordPress soruları (200+ bilgi sorusu)

---

## Kurulum

1. `ai-la-v2.4.8.zip` dosyasını indirin
2. WordPress admin → Eklentiler → Eklenti Yükle → Zip Yükle
3. Etkinleştirin
4. **Ayarlar → Ai-la** sayfasından Groq API key girin

---

## Ayarlar

**Ayarlar → Ai-la** sayfasından:

| Alan | Açıklama |
|---|---|
| Groq API Key | Groq AI entegrasyonu için. Ücretsiz: console.groq.com/keys |

> Key girilmezse keyword modu çalışır — yine de 200+ konuda yardımcı olur.

---

## Desteklenen Eklentiler (Kısmi Liste)

WooCommerce, Elementor, Elementor Pro, Yoast SEO, Rank Math, ACF, Gravity Forms, WPForms, Ninja Forms, Contact Form 7, WPML, Loco Translate, Polylang, TranslatePress, Weglot, WP Rocket, LiteSpeed Cache, W3 Total Cache, WP Super Cache, Autoptimize, Wordfence, UpdraftPlus, Jetpack, MonsterInsights, Mailchimp for WP, WP Mail SMTP, FluentCRM, MemberPress, Paid Memberships Pro, LearnDash, LifterLMS, Tutor LMS, Amelia, Bookly, Dokan, AffiliateWP, CartFlows, Easy Digital Downloads, SearchWP, Slider Revolution, Astra, Divi, GeneratePress, OceanWP, Flatsome, Royal Addons, Essential Addons, Happy Addons, Premium Addons, JetElements, Unlimited Elements, Piotnet Addons

---

## Mimari Notlar

### Actions Sistemi (Gelecek)
Mevcut mimari "Actions" sistemine hazır:
- PHP: `aila_handle_query` → intent router → `route` / `info` / ileride `action`
- JS: `renderByType(data)` → `type: 'route'` / `type: 'info'` / ileride `type: 'action'`

**Planlanan (Faz 2):**
- Logo yükleme — chat'e görsel sürükle, WordPress Media Library'e yükle
- Toplu işlemler — "tüm ürün fiyatlarını %10 artır" gibi komutlar
- Site analizi — SEO skoru, yavaş sayfalar


## Geliştirici

**Ai-la** · WordPress AI Admin Assistant  
Sürüm: 2.4.8
