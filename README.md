# Türk Masalları Derlemesi

On Türk halk masalını, kaynaklarıyla birlikte, okumak için tek sayfada toplayan bir web
sayfası. Programlamaya Giriş dersi vize ödevi.

**Video:** [VİDEO BAĞLANTISI BURAYA]

---

## Nasıl açılır

`index.html` dosyasına **çift tıkla**. Tarayıcıda açılır.

Sunucu, kurulum, internet bağlantısı gerekmez. Sayfa tamamen çevrimdışı çalışır: dışarıdan
yüklenen font, kütüphane, görsel ya da CDN yok.

---

## Ne yapıyor

- **Masal seçme ve gezinme** — Listeden ya da kenar menüden masala tıklanır; önceki/sonraki
  masal düğmeleri vardır. Her masala en fazla iki tıkla ulaşılır.
- **Arama** — Masal başlığında ve metnin içinde anlık arama. Eşleşen kelimeler okuma
  alanında işaretlenir.
- **Etikete göre süzme** — "dev", "aşk", "keloğlan" gibi etiketlerle liste daraltılır.
  Etiketler masal dosyalarının künyesinden toplanır, elle liste tutulmaz; en sık geçenler
  başta gösterilir, kalanlar tek tıkla açılır.
- **Okuma ayarları** — Yazı boyutu (A− / A+, 18–28px), satır aralığı (sıkı / normal / geniş),
  okuma modu (açık / sepya / koyu). Ayarlar `localStorage`'a kaydedilir, tarayıcı izin
  vermezse sayfa yine çalışır.
- **Okuma ilerlemesi** — Sayfanın üstünde üç elma. Okudukça sırayla dolar; masal bitince
  üçüncüsü dolar ve masal listede "okundu" olarak işaretlenir.
- **Duyarlı tasarım** — Masaüstünde iki sütun (kenar menü + okuma alanı), telefonda tek
  sütun ve açılır menü. 360px genişlikte yatay kaydırma yok.
- **Erişilebilirlik** — `lang="tr"`, anlamlı HTML etiketleri, klavye ile tam gezinme,
  görünür odak halkası, `aria-*` etiketleri, `prefers-reduced-motion` desteği.

---

## Masalların seçimi

Ödev 8–12 masal istiyor; bu derlemede **10 masal** var:

1. Keloğlan ve Altın Bülbül
2. Hüsnü Yusuf
3. İncili Çadır
4. Mitişik Kız
5. Keloğlan ile Yılan, Köpek, Kedi ve Balık
6. Öksüz Kız
7. Korkak Adam ve Devler
8. Kırkıncı Oda
9. Üç Turunçlar
10. Üç Oğlan

Liste olduğu gibi korundu; hiçbiri çıkarılmadı, başka masal eklenmedi.

**Çeşitlilik:** Seçim tek bir masal tipine yığılmıyor. Keloğlan'ın yoksul-zeki kahramanlığı
(1, 5), aşk ve kavuşma (2, 9), üvey/öksüz evlat (6), hayvan dostluğu (5), dev masalları
(4, 7), cesaret ve mizah (7), yasak oda ve merak (8), üç kardeş motifi (9, 10) — hepsi ayrı
bir damardan geliyor. Etiketler bu temalara göre verildi.

---

## Masal metinleri nereden geliyor

**Metinler bu projede yazılmadı, yeniden anlatılmadı, özetlenmedi.** Her masal, kaynağından
alındığı gibi duruyor.

Metinler `masallar/` klasöründeki dosyalarda tutulur. Her dosyanın başında künye vardır:

```
---
baslik: Mitişik Kız
kaynak: (derleyen, kitap/site, yıl, bağlantı)
etiketler: dev, kızlar, akıl
---
Masal metni burada...
```

`derle.py` betiği bu dosyaları okur ve `index.html` içindeki `MASALLAR` dizisini üretir.
Metin JSON olarak kaçışlanır; hiçbir kelimesi değişmez. Paragraflar boş satırla ayrılır,
paragraf içindeki satır sonları da korunur (masallardaki karşılıklı konuşmalar alt alta
yazılmış). Her masalın altında sayfada kaynak künyesi görünür.

```bash
python derle.py --iskelet   # eksik masal dosyalarını boş şablon olarak oluşturur
python derle.py             # dosyaları okur, index.html'i günceller, rapor yazdırır
```

Betik Python 3.8+ ile çalışır, hiçbir paket kurulumu gerektirmez. Bir dosya boşsa ya da
yoksa, o masalın metni sayfada `[METİN EKLENECEK]` olarak görünür ve betik bunu sonda
listeler.

**Şu anki durum:** On masalın metni de tam, toplam **13.849 kelime**. Eksik metin yok.

Kaynakların tam listesi ve lisans bilgileri: [`kaynaklar.md`](kaynaklar.md)

---

## Proje klasörü

```
/
├── index.html              # tek dosya: HTML + <style> + <script>
├── derle.py                # masallar/*.md dosyalarını index.html'e gömer
├── masallar/               # masal metinleri (10 dosya, künyeli)
├── gorsel-promptlari/      # sayfadaki her görselin tasarım yönergesi
├── README.md               # bu dosya
├── kaynaklar.md            # masal kaynakları
├── tasarim-notlari.md      # renk, yazı tipi, yerleşim kararlarının gerekçesi
├── kod-haritasi.md         # hangi CSS/JS bölümü ne işe yarar
├── yz-kullanimi.md         # kullanılan yapay zekâ araçları
└── rapor/                  # LaTeX şablonu ve PDF (ayrıca doldurulacak)
```

---

## Yapay zekâ kullanımı

Sayfanın kodu ve tasarımı yapay zekâ yardımıyla yazıldı; masal metinleri yazılmadı.
Ayrıntılı döküm: [`yz-kullanimi.md`](yz-kullanimi.md)

Sayfadaki bütün görseller (kilim şeridi, çini yıldızı, on masal motifi, üç elma) elle
çizilmiş satır içi SVG'dir. Görsel üreten bir yapay zekâ aracı kullanılmadı. Her görselin
tasarım yönergesi `gorsel-promptlari/` klasöründe.

---

**Derleyen:** Oya Meriç Alpay
