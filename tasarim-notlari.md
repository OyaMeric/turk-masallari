# Tasarım Notları

Bu dosya `index.html` sayfasındaki tasarım kararlarının gerekçesini anlatır. Sunumda
"neden böyle yaptın?" sorusunun cevabı burada.

---

## 1. Fikir: "Gökten üç elma düştü"

Türk masallarının çoğu aynı kalıpla kapanır:

> Gökten üç elma düştü: biri anlatana, biri dinleyene, biri de bana.

Bu kalıp masalı **üç kişiye bölüştürür** — anlatan, dinleyen ve okuyan. Sayfanın fikri
buradan çıktı:

> **Bu sayfada, her masalı bitiren "gökten üç elma düştü" kalıbı, okuma ilerlemesinin
> kendisi olur.**

Sayfanın üstündeki ilerleme göstergesi jenerik bir çubuk değil, **üç elma**. Okudukça
elmalar sırayla dolar; masalın sonuna geldiğinde üçüncü elma dolar. Yani ödevin istediği
"okuma ilerlemesi" işlevi, konunun kendi malzemesinden yapıldı.

Okunan masallar listede dolu elma işaretiyle kalır (`localStorage`), böylece sayfa
"nerede kalmıştım" sorusunu da cevaplar.

**Neden bu fikir:** Başka bir masal sitesi de düz bir ilerleme çubuğu koyabilir. Üç elmayı
ilerlemenin kendisi yapmak bu derlemeye özgü, çünkü kalıp Türk masalının kendi kapanışı.

---

## 2. Yerleşim: ikiye bölünmüş sahne

Masaüstünde sayfa **ikiye bölünür**: bir yarısı yerinde durur, öteki yarısı kayar.

- **Sabit yarı:** koyu çini mavisi bir alan. İçinde o an seçili masalın kendi motifi var
  (her masal için ayrı çizilmiş SVG). Masal değişince motif karşı motife yavaşça geçer.
- **Kayan yarı:** parşömen renginde, dar ve sakin bir okuma kolonu.

**Neden:** Masal okumak uzun soluklu bir iş. Sabit yarı atmosferi sürekli ekranda tutar,
okuma kolonu hiç bozulmaz. Ödevin istediği "kenar menü + okuma alanı" iki sütunu da tam
olarak bu.

Tek düzeliği kırmak için **"Masallar" bölümü bu bölünmeyi kırar** ve tam genişlikte akar;
üstünden kilim şeridi geçer.

Telefonda sütunlar tek kolona iner, masal listesi açılır menüye girer, sabit yarı kısa bir
panele dönüşür. 360px'te yatay kaydırma yok.

### Bölümler ve ne iddia ettikleri

| Bölüm | İddiası | Kanıtı |
| --- | --- | --- |
| Açılış | Bu derleme okumak için yapıldı | Başlık, tek cümle, "İlk masalı aç" düğmesi |
| Masallar | On masal, on ayrı tema | Etiketli liste, arama, etikete göre süzme |
| Okuma | Burada okunur, ayarları sende | Masal metni, A−/A+, satır aralığı, üç tema, üç elma |
| Bu derleme üzerine | Metinler kaynaklardan geldi, uydurulmadı | Derleyen notu + her masalın altında kaynak künyesi |
| Alt satır | — | Tek sessiz satır |

---

## 3. Renk paleti

Renkler kilim, çini ve tezhipten alındı. Hepsi `:root` altında CSS değişkeni.

| Değişken | Değer | Nerede | Kontrast |
| --- | --- | --- | --- |
| `--renk-zemin` | `#f3ead9` parşömen | Okuma kolonunun zemini | — |
| `--renk-metin` | `#2a1f17` koyu kahve | Bütün gövde metni | 12.6:1 ✓ |
| `--renk-saha` | `#163a5f` çini mavisi | Sabit yarının alanı | 8.4:1 ✓ |
| `--renk-vurgu` | `#8e2b2b` bordo | Tek eylem düğmesi, bağlantılar | 6.3:1 ✓ |
| `--renk-hardal` | `#8a5f14` hardal | Etiketler, motif detayı | 4.9:1 ✓ |
| `--renk-soluk` | `#6b5a48` | İkincil notlar, kaynak künyesi | 5.4:1 ✓ |

Bir rengin **üzerine** gelen yazı için ayrı değişkenler var; böylece tema değişince zemin ve
yazı birlikte değişiyor:

| Değişken | Nerede | Neden ayrı |
| --- | --- | --- |
| `--renk-vurgu-yazi` | Bordo düğmenin üstündeki yazı | Koyu temada bordo açılıyor, beyaz yazı okunmaz oluyordu |
| `--renk-vurgu-hover` | Düğmenin üzerine gelince | Sabit kodlanmış renk koyu temada ters düşüyordu |
| `--renk-saha-yazi` | Çini alanının üstündeki yazı ve motifler | Koyu temada motif rengi kâğıt rengine bağlıydı, görünmez oluyordu |

Üç tema da tarayıcıda ölçüldü: **açık, sepya ve koyu temada her metin WCAG AA eşiğinin
(4.5:1) üstünde.** Motiflerin çini zeminine kontrastı en düşük temada 9.7:1.

**Oran kuralı:** Tek zemin, tek metin rengi, tek vurgu. Bordo **sadece** eylem düğmesinde ve
bağlantılarda görünür; başlıklar da gövdeyle aynı kahverengide. Renk, gerçekten dikkat
çekmesi gereken yere saklandı.

**Üç okuma modu:** açık (parşömen), sepya (daha sıcak kâğıt), koyu (gece okuması). Üçü de
aynı değişken isimlerini yeniden tanımlar; bu yüzden tema değiştirmek tek satır iş.

---

## 4. Yazı tipi

Harici font yasak, bu yüzden **yalnızca sistemde kurulu yazı tipleri**. Sayfanın tamamında
**tek bir yazı tipi** kullanılıyor:

```css
--yazi: Georgia, "Palatino Linotype", "Book Antiqua", "Times New Roman", serif;
```

Başlıklar, masal metni, düğmeler, etiketler, arama kutusu — hepsi aynı serif yığınında.

**Neden tek yazı tipi:** Sayfa bir kitap sayfası gibi okunsun diye. Arayüz parçalarını ayrı
bir sans-serif ile yazmak onları "uygulama" gibi gösteriyor, metni ise ayrı bir yere
itiyordu. Tek yazı tipiyle düğme de, masal da aynı sayfanın parçası gibi duruyor.

Düğme ve giriş alanları tarayıcıdan gelen kendi yazı tipini kullanır; tek satırlık bir
kuralla onlara da devrettirildi:

```css
button, input, select, textarea { font-family: inherit; }
```

**Altı boyut adımı, fazlası yok.** Sayfanın hiçbir yerinde bu altısının dışında bir yazı
boyutu kullanılmaz:

| Adım | Boyut | İş |
| --- | --- | --- |
| `--tip-kucuk` | 14–15px | Etiket, alt satır, kaynak künyesi, ayar yazıları |
| `--tip-orta` | 16–17px | Düğmeler, arama kutusu, kenar menü, derleme notu |
| `--tip-govde` | 18–28px | Masal metni (varsayılan 20px, okur değiştirebilir) |
| `--tip-ara` | 22–26px | Giriş cümlesi, masal listesi satırları, imza |
| `--tip-baslik` | 32–44px | Bölüm başlıkları |
| `--tip-dev` | 38–52px | Sayfanın tek `h1`'i |

Tarayıcıda ölçüldüğünde sayfada tam **6 farklı yazı boyutu** ve **1 yazı tipi** çıkıyor.

Masal metni: satır aralığı **1.7**, sütun genişliği **66 karakter**. İkisi de ödevin verdiği
okunabilirlik aralığının içinde (1.7 ve 60–75 karakter).

---

## 5. Motifler — hepsi elle çizildi

Harici görsel yok. Sayfadaki her görsel **satır içi SVG** ya da CSS ile üretildi:

- **Kilim şeridi:** tekrar eden eşkenar dörtgen ve çengel motifi, `<pattern>` ile.
- **Çini yıldız:** sekiz kollu yıldız, açılış sahnesinde.
- **Masal motifleri:** on masalın her birine bir motif — bülbül, çadır, inci, dev, yılan,
  balık, iğ, kırk kapı, turunç, üç ok. Hepsi aynı çizim diliyle: tek çizgi kalınlığı,
  geometrik, palet renkleri. `<symbol>` + `<use>` olarak bir kez tanımlanıp tekrar
  kullanılıyor, böylece dosya şişmiyor.
- **Üç elma:** ilerleme göstergesi. Dolum, basit bir `clip-path` yüksekliğiyle çiziliyor
  (sunumda anlatması kolay olsun diye `stroke-dasharray` gibi numaralar kullanılmadı).

Hiçbir motif telifli bir karakteri, çizimi ya da film karesini taklit etmiyor.

---

## 6. Bilinçli olarak yapılmayanlar

Jenerik "yapay zekâ sayfası" görüntüsünden kaçınmak için şunlar sayfada **yok**:

- Gradyan (ne zeminde, ne düğmede)
- Duran nesnede gölge veya parıltı
- İnce ayırıcı çizgiler, 1px çerçeveli kutular — yerine boşluk ve ton farkı
- İkon başlıklı özellik kartları, aynı kartların ızgarası
- Başlığın üstünde küçük etiket ("Yeni ·" gibi)
- `01 / 02 / 03` biçiminde numaralandırma
- Küçük, harfleri aralanmış BÜYÜK HARF etiketler
- Emoji, cam/bulanıklık efekti, yüzen hap şeklinde menü
- Mor/indigo renkler, hazır tema paleti

Süsü kaldırınca kalan boşluk başka süsle doldurulmadı: **daha büyük tipografi**, **dolu renk
alanları** ve **tam içerik** ile dolduruldu.

---

## 7. Erişilebilirlik

- `lang="tr"`, anlamlı HTML: `header`, `nav`, `main`, `article`, `aside`, `button`
- Her denetim klavyeyle çalışır, odak halkası görünür (`:focus-visible`)
- İkon-only düğmelerde `aria-label`; açık masalda `aria-current="true"`
- Arama sonucu sayısı `aria-live="polite"` ile duyurulur
- İlerleme göstergesi `role="progressbar"` + `aria-valuenow`
- `prefers-reduced-motion` açıkken bütün geçişler kapanır, içerik yerinde kalır
- Metin–zemin kontrastı üç temada da AA

---

## 8. Metinler nereden geliyor

**Masal metinlerini bu sayfayı yapan yapay zekâ yazmadı.** Metinler öğrencinin kaynaklardan
aldığı dosyalardan geliyor:

```
masallar/01-keloglan-ve-altin-bulbul.md
masallar/02-husnu-yusuf.md
... (10 dosya)
```

Her dosyanın başında künye var (`baslik`, `kaynak`, `etiketler`), altında masalın kendisi.
`derle.py` betiği bu dosyaları okur ve `index.html` içindeki `MASALLAR` dizisini üretir;
metin JSON olarak kaçışlanır, **hiçbir kelimesi değişmez**. Her masalın altında sayfada
kaynak künyesi görünür.

Bir dosya boşsa o masalın metni `[METİN EKLENECEK]` olarak kalır — betik bunu sonda raporlar.

---

## 9. Değerlendirilen ve elenen seçenekler

Yerleşim için üç seçenek düşünüldü:

1. **Düzensiz boyutlarda fotoğraf ızgarası** — galeri duvarı gibi, her görsel ayrı boyutta.
   Elendi: çok sayıda fotoğraf gerektiriyor, ödevde harici görsel yasak.
2. **Tam ekran tek fotoğraf** — açılışta ekranı kaplayan bir görsel, başlık altta.
   Elendi: aynı sebep.
3. **İkiye bölünmüş sahne** — bir yarı yerinde durur, öteki kayar. **Seçildi**, çünkü sabit
   yarı elle çizilmiş bir motifle de doldurulabiliyor ve ödevin istediği "kenar menü +
   okuma alanı" iki sütununa birebir oturuyor.

Renk ve yazı tipi için de iki seçenek elendi:

- **Lacivert + pembe palet:** konuya yabancı. Kilim, çini ve tezhipten gelen renkler
  tercih edildi. Paletin *yapısı* korundu: tek zemin, tek metin rengi, tek vurgu.
- **Google Fonts üzerinden yüklenen serif yazı tipleri:** ödev harici font yüklemeyi
  yasakladığı için elendi, sistem serif yığınına geçildi.

Bir kural da uygulanamadı: "sayfada en az dört gerçek fotoğraf bulunsun". Harici görsel
yasağı daha önce geldiği için, yerine aynı çizim dilinde elle çizilmiş SVG motifler
kullanıldı.
