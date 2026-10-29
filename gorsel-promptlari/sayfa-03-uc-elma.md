# Üç elma — okuma ilerlemesi

**Sayfadaki yeri:** Üst çubuğun ortasında, sayfa boyunca görünür. Ayrıca masal listesinde
okunmuş masalların önünde küçük dolu elma olarak tekrar eder.
**SVG kimliği:** `<path id="elma-yol">`, 24×28 birim
**Üretim:** Elle çizildi, yapay zekâ görsel üreticisi kullanılmadı.

## Tasarım prompt'u

> Üç elmayı yan yana, sadece dış hatlarıyla çiz. Elma gövdesi iki yandan hafif basık bir
> daire, üstünde sağa doğru kıvrılan kısa bir sap. Yaprak yok, parlama yok, yüz yok.
> Elmalar birbirinin aynısı olsun; sıralı tekrar, çeşitlilikten daha önemli.
> Doluluk aşağıdan yukarıya yükselen düz bir kesme çizgisiyle gösterilsin — elma suyla
> dolar gibi. Dolu kısım bordo, boş kısım yalnızca ince çizgi.

## Geometri

- Gövde: (12,7.5)'ten başlayan iki Bézier yayı, en geniş yeri y≈16, taban y≈25.6
- Sap: (12,7.5) → (16,1.8) arası tek yay
- Üç elma x = 1, 29, 57 konumlarında, toplam kutu 84 × 30
- Doluluk: her elma için bir `<clipPath>` dikdörtgeni; JS yalnızca `y` ve `height`
  değerlerini değiştirir

## Neden bu motif

Türk masallarının kapanış kalıbı: *"Gökten üç elma düştü: biri anlatana, biri dinleyene,
biri de bana."* Kalıp masalı üç kişiye bölüştürür. Sayfa bu bölüşmeyi ilerleme göstergesine
çevirdi: okudukça elmalar sırayla dolar, üçüncüsü dolduğunda masal biter.

Jenerik bir ilerleme çubuğu yerine bu seçildi, çünkü çubuk her sitede var; üç elma yalnızca
bu derlemede var.
