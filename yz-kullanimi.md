# Yapay Zekâ Kullanımı

Bu projede yapay zekânın ne yaptığı ve **ne yapmadığı**.

---

## Kullanılan araç

| Araç | Sürüm / model | Ne için |
| --- | --- | --- |
| Claude Code (Anthropic) | Opus 5 | Sayfanın HTML/CSS/JavaScript kodu, `derle.py` betiği, tasarım kararları ve belge dosyaları |

Tasarım kararlarında, jenerik sayfa kalıplarından (gradyan, ikon kartları, ince ayırıcı
çizgiler, küçük büyük-harf etiketler, hazır kart ızgaraları) kaçınmayı şart koşan bir kural
seti kullanıldı. Hangi seçeneklerin değerlendirilip neden elendiği `tasarim-notlari.md`
dosyasının 9. bölümünde yazılı.

---

## Yapay zekânın YAPMADIĞI şeyler

**1. Masal metinleri.** Hiçbir masal metni yapay zekâ ile yazılmadı, yeniden anlatılmadı,
özetlenmedi ya da "tamamlanmadı". Metinler öğrencinin derlediği dosyadan geldi; yapay zekânın
tek yaptığı, bu dosyayı on ayrı masal dosyasına **bölmek** ve `derle.py` ile sayfaya
**kelimesi değişmeden** gömmek oldu.

Bölme sırasında metne hiçbir ekleme yapılmadı; yalnızca `## 1. Başlık` biçimindeki bölüm
başlıkları ve bölümleri ayıran `---` satırları ayıklandı. Dosyanın sonundaki
"Eksik / Dikkat Edilmesi Gerekenler" notları da masal metnine karışmasın diye ayrıldı; o
notlar `kaynaklar.md` içine taşındı.

Gömülen toplam: 10 masal, 13.849 kelime, 353 paragraf. Eksik metin yok.

**2. Kaynaklar.** Hiçbir kaynak künyesi yapay zekâ tarafından üretilmedi veya tahmin
edilmedi. Kaynaklar `kaynaklar.md` ve masal dosyalarının künyesinde, doğrulanarak elle
girilir.

**3. Görseller.** Sayfada görsel üreten bir yapay zekâ aracı (Midjourney, DALL·E, Stable
Diffusion vb.) **kullanılmadı**. Bütün görseller elle yazılmış satır içi SVG'dir.

---

## Görsel prompt'ları

Ödev, yapay zekâ ile görsel üretilirse prompt'ların yazılmasını istiyor. Bu projede görsel
üreten bir araç kullanılmadı; yine de her görselin **tasarım yönergesi** (hangi kurallara
göre çizildiği) `gorsel-promptlari/` klasöründe tutuluyor:

| Dosya | Görsel | Sayfadaki yeri |
| --- | --- | --- |
| `00-cizim-dili.md` | Ortak çizim kuralları | Bütün motifler |
| `sayfa-01-cini-yildiz.md` | Sekiz kollu çini yıldızı | Açılış sahnesi, sağ yarı |
| `sayfa-02-kilim-seridi.md` | Kilim şeridi | İki bölüm ayıracı |
| `sayfa-03-uc-elma.md` | Üç elma | Üst çubuk, ilerleme göstergesi |
| `masal-01` … `masal-10` | On masal motifi | Masallar bölümü, motif alanı |

Her dosyada: görselin sayfadaki yeri, SVG kimliği, tasarım prompt'u, geometri değerleri ve
"neden bu motif" gerekçesi var.

---

## Yapay zekânın YAPTIĞI şeyler

- `index.html` içindeki HTML yapısı, CSS ve JavaScript
- `derle.py` betiği
- Renk paleti, yazı tipi ölçeği ve yerleşim kararları (gerekçeleri `tasarim-notlari.md`)
- On masal motifinin, kilim şeridinin ve çini yıldızının SVG çizimleri
- `README.md`, `kaynaklar.md` şablonu, `kod-haritasi.md`, `tasarim-notlari.md` ve
  `gorsel-promptlari/` dosyaları
- Sayfanın tarayıcıda test edilmesi (1280px ve 360px genişlik, konsol hatası kontrolü,
  arama/gezinme/ayar/ilerleme işlevlerinin denenmesi)

---

## Öğrencinin kendi yaptığı şeyler

- Masal listesinin seçimi
- Masal metinlerinin kaynaklardan bulunup `masallar/` klasörüne konulması
- Kaynakların doğrulanması ve künyelerin girilmesi
- `rapor/` klasöründeki rapor
- Sunum videosu

---

**Derleyen:** Oya Meriç Alpay
