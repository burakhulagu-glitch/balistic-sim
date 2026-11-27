# Material Creator ve Ballistic Simulator

TarayÄ±cÄ±da, kurulum gerektirmeden Ã§alÄ±ÅŸan iki programdÄ±r. Sunucuya veri gÃ¶ndermez;
kullanÄ±cÄ±nÄ±n oluÅŸturduÄŸu malzemeler ve arayÃ¼z ayarlarÄ± yalnÄ±z kendi tarayÄ±cÄ±sÄ±nÄ±n
yerel deposunda tutulur.

| Program | SÃ¼rÃ¼m | Dosya | Ne yapar |
|---|---|---|---|
| Material Creator (MC) | 3.8.1 | `mc.html` | Kompozit, hÃ¼cresel ve kafes malzemeleri homojenleÅŸtirir: tek yÃ¶nlÃ¼ tabaka, partikÃ¼l, kÄ±sa elyaf, dokuma kumaÅŸ, petek ve kafes modÃ¼lleri; kafeslerde Ä±sÄ±l iletkenlik. TaÅŸÄ±nabilir malzeme kartÄ± Ã¼retir. |
| Ballistic Simulator (BS) | 2.12.3 | `bs.html` | Analitik Ã§ok atÄ±ÅŸlÄ± delinme modeli: metal katmanlarda kesme tÄ±kacÄ±, kompozit katmanlarda Wen baÄŸÄ±ntÄ±sÄ±, seramiklerde Tate modeli. V50, artÄ±k hÄ±z, NIJ Ã¶n deÄŸerlendirmesi ve hÄ±z ile enerji zaman geÃ§miÅŸi. |

`index.html` iki programÄ± aÃ§an kabuk sayfadÄ±r.

## KullanÄ±m

SayfayÄ± tarayÄ±cÄ±da aÃ§mak yeterlidir. Yerel olarak Ã§alÄ±ÅŸtÄ±rmak iÃ§in klasÃ¶rÃ¼ basit bir
HTTP sunucusuyla servis etmek gerekir (dosya yolundan aÃ§Ä±ldÄ±ÄŸÄ±nda bazÄ± tarayÄ±cÄ±lar
modÃ¼l ve wasm yÃ¼klemesini engeller):

```
python -m http.server 8000
```

## Birlikte kullanÄ±m

MC'nin Ã¼rettiÄŸi malzeme kartÄ± BS'e aktarÄ±lÄ±r; BS karttan yalnÄ±z gereken alanlarÄ± okur ve
eksik alan varsa hesaplamayÄ± reddeder. BS 2.11.0'dan sonra ardÄ±ÅŸÄ±k kompozit katmanlar tek
bir laminatta birleÅŸtirilir, bÃ¶ylece katman bÃ¶lme yapaylÄ±ÄŸÄ± ortadan kalkar.

## DoÄŸrulama

- MC'nin her modÃ¼lÃ¼ aynÄ± girdilerle Ansys Material Designer ile karÅŸÄ±laÅŸtÄ±rÄ±lmÄ±ÅŸtÄ±r.
- BS, 3 mm plakalarda altÄ± ardÄ±ÅŸÄ±k 9Ã—19 mm atÄ±ÅŸÄ±n LS-DYNA Ã§Ã¶zÃ¼mlerine uydurulmuÅŸ;
  7,62Ã—51 mm serisi, kÃ¶r seri ve yayÄ±mlanmÄ±ÅŸ deneylerle denetlenmiÅŸtir.
- BS iÃ§inde 52 Ã¶z test bulunur; SÃ¼rÃ¼m penceresinden Ã§alÄ±ÅŸtÄ±rÄ±lÄ±r.

ProgramlarÄ±n sonuÃ§larÄ± Ã¶n tasarÄ±m ve eÄŸitim iÃ§indir; doÄŸrulanmÄ±ÅŸ sonlu eleman Ã§Ã¶zÃ¼mÃ¼ ve
atÄ±ÅŸ testi yerine geÃ§mez.

## Kaynak

Burak HÃ¼lagÃ¼. ProgramlarÄ±n geliÅŸtirilmesi, doÄŸrulanmasÄ± ve balistik uygulamasÄ± ilgili
makalede anlatÄ±lmÄ±ÅŸtÄ±r.
