# Kod Haritası

Sunumda "burada ne oluyor?" sorusunun cevabı. `index.html` tek dosya; içinde üç kısım var:
HTML yapısı, `<style>` içindeki CSS ve `<script>` içindeki JavaScript. Her kısım numaralı
yorum satırlarıyla bölünmüş.

---

## CSS bölümleri

| # | Bölüm | Ne işe yarıyor |
| --- | --- | --- |
| 1 | `DEĞİŞKENLER` | Bütün renkler, boşluklar ve yazı boyutları `:root` altında tanımlı. Sayfanın hiçbir yerinde doğrudan renk kodu yazılmaz. Altında sepya ve koyu temalar aynı değişkenleri yeniden tanımlar — tema değiştirmek bu yüzden tek satırlık iş. |
| 2 | `SIFIRLAMA VE TEMEL` | Tarayıcı varsayılanlarını temizler, gövde yazı tipini ve odak halkasını kurar. "İçeriğe atla" bağlantısı burada. |
| 3 | `ÜST ÇUBUK` | Sayfanın üstünde duran (sticky) çubuk: marka, üç elma göstergesi, gezinme bağlantıları. |
| 4 | `AÇILIŞ` | İkiye bölünmüş sahne. Sol yarı kayar, sağ yarı `position: sticky` ile yerinde durur. |
| 5 | `KİLİM ŞERİDİ` | Bölümleri ayıran desenli şerit. |
| 6 | `MASALLAR BÖLÜMÜ` | Arama kutusu, etiket düğmeleri ve masal listesi. Solda yerinde duran motif alanı. |
| 7 | `OKUMA BÖLÜMÜ` | Solda kenar menü (ray) + okuma ayarları, sağda masal metni. Metin sütunu `--metin-olcu` ile 66 karakterde tutulur. |
| 8 | `DERLEME NOTU` | Ortada duran dar mektup kolonu. |
| 9 | `ALT SATIR` | Üç sütunlu tek satırlık alt bilgi. |
| 10 | `GİRİŞ HAREKETİ` | `.beliren` sınıfı: parçalar başta saydam ve 20px aşağıda; `.gorundu` eklenince yerine oturur. |
| 11 | `TELEFON VE TABLET` | `@media` kuralları: 960px altında tek kolon ve açılır menü, 420px altında daha dar boşluklar. En sonda `prefers-reduced-motion` bütün geçişleri kapatır. |

---

## JavaScript bölümleri

| # | Bölüm | Ne işe yarıyor |
| --- | --- | --- |
| 1 | `MASAL VERİSİ` | `const MASALLAR = [...]` — on masalın başlığı, etiketleri, kaynağı ve paragrafları. **Bu bloğu `derle.py` üretir**, elle düzenlenmez. |
| 2 | `KISA YOLLAR` | Üç küçük yardımcı: `bul()` (seçici), `yeni()` (öğe üretir, `textContent` ile), `kucuk()` (Türkçe'ye uygun küçük harf — İ/ı farkı için). |
| 3 | `DURUM` | Sayfanın o anki hâli tek nesnede: açık masal, arama yazısı, seçili etiket, yazı boyutu, satır aralığı, tema, okunanlar. |
| 4 | `AYARLARI SAKLAMA` | `localStorage`'a yazar ve okur. İkisi de `try/catch` içinde: gizli sekmede izin olmayabilir, o zaman sayfa varsayılanlarla devam eder. |
| 5 | `SÜZME` | Arama ve etiket birlikte çalışır. Bir masal, hem etikete uyuyorsa hem de aranan kelime başlığında ya da metninde geçiyorsa listede kalır. |
| 6 | `MASAL LİSTESİ` | Listeyi sıfırdan çizer. Okunmuş masalların önüne dolu elma koyar, açık masalın altında kısa tanıtım gösterir, sonuç sayısını `aria-live` ile duyurur. |
| 7 | `ETİKET SÜZGECİ` | Etiketler veriden toplanır; elle liste tutulmaz. Her etiketin kaç masalda geçtiği sayılır, çok geçenler başa alınır. Otuz bir etiket olduğu için başta yalnızca ilk on gösterilir, "N etiket daha" düğmesi kalanı açar. |
| 8 | `MASAL AÇMA` | Seçilen masalı okuma alanına yazar. Her paragraf kendi `<p>`'si olur; paragraf içindeki satır sonları CSS'teki `white-space: pre-line` sayesinde kaynaktaki gibi görünür. Arama varsa `paragrafCiz()` eşleşmeleri `<mark>` ile işaretler — **`innerHTML` kullanılmaz**, parçalar metin düğümü olarak eklenir. |
| 9 | `MOTİF DEĞİŞTİRME` | On motif SVG içinde üst üste durur; fonksiyon yalnızca `acik` sınıfını taşır, geçişi CSS yapar. |
| 10 | `ÖNCEKİ / SONRAKİ` | Düğmelerin yazısını ve `disabled` durumunu günceller, tıklamaları bağlar. Listenin başında ve sonunda düğmeler kapanır. |
| 11 | `KENAR MENÜ` | Okuma bölümündeki ray listesini çizer; açık masalı `aria-current` ile işaretler. |
| 12 | `OKUMA AYARLARI` | Yazı boyutu (18–28px), satır aralığı ve tema. Üçü de CSS değişkenini değiştirir, sonra kaydeder. |
| 13 | `ARAMA` | Arama kutusunu dinler, her tuşta listeyi ve metin vurgusunu yeniler. |
| 14 | `OKUMA İLERLEMESİ` | Metin kutusunun ekrana göre konumundan okunan oranı hesaplar, üç elmayı doldurur. Doluluk `<clipPath>` dikdörtgeninin `y` ve `height` değeriyle çizilir. Oran %98'i geçince masal "okundu" sayılır. |
| 15 | `TELEFONDA AÇILIR MENÜ` | 960px altında masal listesi kapalı başlar; düğme `aria-expanded` ile açıp kapatır. |
| 16 | `GİRİŞ HAREKETİ` | `IntersectionObserver` ile bölüm parçaları ekrana girdikçe sırayla belirir. Tarayıcı desteklemezse hepsi doğrudan görünür. |
| 17 | `BAŞA DÖN` | Alt satırdaki bağlantı sayfanın başına kaydırır. |
| 18 | `BAŞLAT` | Yukarıdakileri sırayla çağırır: ayarları yükle → uygula → düğmeleri bağla → listeleri çiz → ilk masalı aç → kaydırmayı dinle. |

---

## Üç şeyi sunumda ayrıca anlatmaya değer

**1. Neden `innerHTML` yok.** Arama vurgusu için metni HTML olarak birleştirmek kolay olurdu
ama masal metni dışarıdan gelen bir veri; içinde `<` geçerse tarayıcı onu etiket sanar.
Bunun yerine metin parçaları `document.createTextNode()` ile, vurgular `<mark>` öğesi olarak
tek tek ekleniyor. Hem güvenli hem de ödevin istediği yöntem.

**2. Neden `try/catch`.** `localStorage` her ortamda çalışmaz (gizli sekme, kapalı izin,
dosyadan açılan bazı sayfalar). Hata yakalanmazsa sayfa tamamen durur. Yakalandığında
ayarlar kaydedilmez ama sayfa çalışmaya devam eder.

**3. Neden motifler üst üste duruyor.** Tek bir `<use>` öğesinin hedefini JavaScript ile
değiştirmek yerine on motif baştan SVG içinde duruyor ve sadece `acik` sınıfı taşınıyor.
Böylece geçişi CSS yapıyor, JavaScript tarafı iki satıra iniyor ve iki motif geçiş sırasında
gerçekten birbirine karışıyor.
