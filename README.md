# Material Creator ve Ballistic Simulator

Tarayıcıda, kurulum gerektirmeden çalışan iki programdır. Sunucuya veri göndermez;
kullanıcının oluşturduğu malzemeler ve arayüz ayarları yalnız kendi tarayıcısının
yerel deposunda tutulur.

| Program | Sürüm | Dosya | Ne yapar |
|---|---|---|---|
| Material Creator (MC) | 3.8.0 | `mc.html` | Kompozit, hücresel ve kafes malzemeleri homojenleştirir: tek yönlü tabaka, partikül, kısa elyaf, dokuma kumaş, petek ve kafes modülleri; kafeslerde ısıl iletkenlik. Taşınabilir malzeme kartı üretir. |
| Ballistic Simulator (BS) | 2.12.1 | `bs.html` | Analitik çok atışlı delinme modeli: metal katmanlarda kesme tıkacı, kompozit katmanlarda Wen bağıntısı, seramiklerde Tate modeli. V50, artık hız, NIJ ön değerlendirmesi ve hız ile enerji zaman geçmişi. |

`index.html` iki programı açan kabuk sayfadır.

## Kullanım

Sayfayı tarayıcıda açmak yeterlidir. Yerel olarak çalıştırmak için klasörü basit bir
HTTP sunucusuyla servis etmek gerekir (dosya yolundan açıldığında bazı tarayıcılar
modül ve wasm yüklemesini engeller):

```
python -m http.server 8000
```

## Birlikte kullanım

MC'nin ürettiği malzeme kartı BS'e aktarılır; BS karttan yalnız gereken alanları okur ve
eksik alan varsa hesaplamayı reddeder. BS 2.11.0'dan sonra ardışık kompozit katmanlar tek
bir laminatta birleştirilir, böylece katman bölme yapaylığı ortadan kalkar.

## Doğrulama

- MC'nin her modülü aynı girdilerle Ansys Material Designer ile karşılaştırılmıştır.
- BS, 3 mm plakalarda altı ardışık 9×19 mm atışın LS-DYNA çözümlerine uydurulmuş;
  7,62×51 mm serisi, kör seri ve yayımlanmış deneylerle denetlenmiştir.
- BS içinde 52 öz test bulunur; Sürüm penceresinden çalıştırılır.

Programların sonuçları ön tasarım ve eğitim içindir; doğrulanmış sonlu eleman çözümü ve
atış testi yerine geçmez.

## Kaynak

Burak Hülagü. Programların geliştirilmesi, doğrulanması ve balistik uygulaması ilgili
makalede anlatılmıştır.
