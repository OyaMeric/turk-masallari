# Açılış — çini yıldızı

**Sayfadaki yeri:** Açılış sahnesinin sağ yarısı; koyu çini mavisi alanın ortasında,
sayfanın en büyük görseli. Masaüstünde sayfa kaydıkça yerinde durur.
**SVG kimliği:** `<symbol id="m-cini">`, viewBox `0 0 240 240`
**Üretim:** Elle çizildi, yapay zekâ görsel üreticisi kullanılmadı.

## Tasarım prompt'u

> Selçuklu geleneğindeki sekiz kollu yıldızı tek çizgiyle çiz. Yıldızın içine tam ortalanmış
> bir çember, çemberin içine uçları yukarı-aşağı bakan bir baklava dilimi yerleştir. Tam
> merkeze dolu küçük bir daire koy. Dört katman da aynı merkezden büyüsün: yıldız → çember →
> baklava → nokta. Çizgi kalınlığı dört katmanda da aynı olsun. Zemin koyu çini mavisi,
> çizgi parşömen rengi.

## Geometri

- Dış yıldız: 8 kol, merkez (120,120), uzun yarıçap 110, kısa yarıçap ~62
- Çember: r = 62
- Baklava: köşeler (120,58) · (155,120) · (120,182) · (85,120)
- Merkez nokta: r = 16, dolu
- `stroke-width="2.4"`, `fill="none"` (merkez nokta hariç)

## Neden bu motif

Sekiz kollu yıldız, Anadolu çini ve ahşap işçiliğinin en yaygın motifi. Sayfanın açılışında
"bu bir Türk masalı derlemesi" cümlesini tek görselle kuruyor. İçe doğru küçülen dört katman,
masalların iç içe geçen yapısına da denk düşüyor: her masalın içinde başka bir masal var.
