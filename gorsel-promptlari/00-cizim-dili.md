# Ortak çizim dili

On masal motifi, çini yıldızı ve kilim şeridi **tek bir çizim dilini** paylaşır. Amaç,
motiflerin ayrı ayrı çizilmiş olmalarına rağmen aynı elden çıkmış görünmesi.

## Genel prompt

> Türk kilim, çini ve tezhip geleneğinden beslenen, tek çizgi kalınlığında, geometrik,
> düz (flat) bir motif ailesi çiz. Her motif kare bir çerçeveye otursun, ortalansın ve
> çerçevenin kenarlarına değmesin. Çizgiler eşit kalınlıkta olsun; gölge, gradyan, doku
> ve perspektif kullanma. Dolgu yalnızca bir ya da iki vurgu parçasında olsun — genelde
> bir yıldız, bir nokta ya da bir göz. Motifler bir masalı resimlemez, **işaret eder**:
> hikâyeyi anlatmaz, hatırlatır.

## Ortak çizim kuralları
- viewBox `0 0 120 120`, kare çerçeve
- `fill="none"`, `stroke="currentColor"`, `stroke-width="2.4"`
- Dolgu yalnızca vurgu parçalarında (`fill="currentColor"`)
- Renk CSS'ten gelir: çini mavisi zemin üzerine parşömen rengi çizgi
- Gölge, gradyan, doku, perspektif yok; düz ve geometrik
- Çizim kutunun %66'sını kaplar, ortalanır

## Neden bu dil

- **Tek çizgi kalınlığı:** kilim dokumasında da çizgi kalınlığı ipliğin kalınlığıdır,
  değişmez. Aynı kuralı motiflere taşıdım.
- **Geometrik:** çini ve tezhip, serbest çizimden çok pergel-cetvel işidir.
- **Dolgu az:** sayfada renk zaten az kullanılıyor; motifin içi dolarsa çini alanın
  sakinliği bozulur.
- **Resimlemek yerine işaret etmek:** masalın olayını çizmek okuru metinden önce
  yönlendirir. Motif sadece "hangi masaldayız" sorusuna cevap verir.

## Telif

Hiçbir motif telifli bir karakteri, çizimi, film karesini ya da yayımlanmış bir
illüstrasyonu taklit etmiyor. Hepsi bu proje için çizildi.
