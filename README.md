# turkiye_2025_nufus_tahmini

Veri 2009-2024 yılından itibaren, 2025'i tahmin et

-> veriler 2009dan itibaren alındı çünkü bazıları daha eski olsa da karşılaştırılabilir olması için
-> göç verisi de 2016 dan itibaren mevcut olduğu için o şekilde alındı

-> neden doğurganlık hızı değil de kaba doğum hızını kullandık, çünkü tahmini toplam nüfus üzerine kurguladık, kaba doğumun tanımı: "belli bir yıl içinde her bin nüfus başına düşen canlı doğum sayısı" olarak tanılanmaktadır. doğurganlık hızı ise "belli bir yıl içinde 15-44 yaş grubunda her bin kadın başına düşen canlı doğan çocuk sayısı" olarak tanımlanmaktadır (TÜİK Doğum İstatistikleri, 2024, Haber Bülteni)
-> ayrıca doğurganlık hızı yıllar arasında drametik değişimler göstermez ve stabil bir yapı sergilerken, kabadoğum kısavadeli etkileri daha iyi bir şekilde yansıtmaktadır. 
-> TÜİK, ADNKS'de kaba doğum hızını her yıl çok net güncellerken, doğurganlık hızı daha karmaşık anketlerle (MERNİS, ADNKS, Türkiye Nüfus ve Sağlık Araştırması) veya projeksiyonlarla revize edilmektedir.
-> Kaba doğum hızı kısa vadede kullanılırken, doğurganlık hızı uzun vadede daha etkin kullanılmaktadır. 
-> Kaba doğum hızı sonuç, doğurganlık hızı ise sebeptir diyebiliriz.

Kullanılan bültenler:
- Adrese Dayalı Nüfus Kayıt Sistemi Sonuçları, 2024 https://veriportali.tuik.gov.tr/tr/press/53783
- Doğum İstatistikleri, 2024 https://veriportali.tuik.gov.tr/tr/press/54196
- Ölüm ve Ölüm Nedeni İstatistikleri, 2024 https://veriportali.tuik.gov.tr/tr/press/54195
- Uluslararası Göç İstatistikleri, 2024 https://veriportali.tuik.gov.tr/tr/press/54083
  
Kullanılan değişkenlere ait tablolar:
- Toplam Nüfus (Yıllara göre il nüfusları, 2000-2024) -> Adrese Dayalı Nüfus Kayıt Sistemi Sonuçları, 2024
- Kaba Doğum Hızı (İllere göre kaba doğum hızı, 2009-2024) -> Doğum İstatistikleri, 2024
- Kaba Ölüm Hızı (Temel ölümlülük göstergeleri, 2009-2024) -> Ölüm ve Ölüm Nedeni İstatistikleri, 2024
- Nüfus Artış Hızı (Yıllara göre illerin yıllık nüfus artış hızı ve nüfus yoğunluğu, 2007-2024) -> Adrese Dayalı Nüfus Kayıt Sistemi Sonuçları, 2024
- Net Göç (İllere ve vatandaşlığa göre Türkiye'ye gelen ve Türkiye'den giden göç, 2016-2024) -> Uluslararası Göç İstatistikleri, 2024

Metaveri
- Yıllara göre il nüfuslarının toplamı bize yıllık toplam nüfusu niceliksel olarak ölçer ve bu veri "nufus_data/Nufus" olarak adlandırılmıştır. 
- İllere göre kaba doğrum hızı yıl içinde her bin nüfus başına düşen canlı doğum sayısını oransal olarak ölçer ve bu veri "dogum_hizi/Dogum_Hizi" olarak adlandırılmıştır. 
- Temel ölümlülük göstergelerinde yer alan Kaba Ölüm Hızı yıl içinde her bin nüfus başına düşen ölüm sayısını oransal olarak ölçer ve bu veri "olum_hizi/Olum_Hizi" olarak adlandırılmıştır. 
- Yıllara göre illerin yıllık nüfus artış hızı ve nüfus yoğunluğu tablosunda yer alan oranlar iki sayım tarihi arasındaki dönemde her 1000 nüfus için yıllık artan nüfus olduğu için, iki yıl arasında gerçekleşen değişim oranları ikinci yılın artış hızı olarak düşünülerek yıllık hale getirildi ve "artis_hizi/Artis_Hizi" olarak adlandırılmıştır. (Örneğin; 2008-2009 yılları arasında 14.5 olarak ölçülen artış 2009 yılına ait olarak değerlendirilmiştir)
- Net göç "İllere ve vatandaşlığa göre Türkiye'ye gelen ve Türkiye'den giden göç" tablosunda yurt dışından gelen ve yurt dışına giden göç arasındaki sayısal fark olarak ölçülmektedir ve 2016 yılı ve sonrasına ait veriler bulunmaktadır ve bu veri "goc_data/Net_Goc" olarak adlandırılmıştır.



Öncelikle doğal nüfus artışını bulmak için doğum hızından ölüm hızını çıkardık. 
Net göç artış oranını bulabilmek için toplam yıllık net göçü, toplam nüfus nüfusuna oranladık ve binle çarptık, böylece yıl içinde her bin nüfus başına düşen net göç sayısını oransal olarak elde etmiş olduk.
Ancak veriler 2016 yılı öncesi eksik bulunduğundan tamamlanması gerekmekteydi. Bu kısımları doldurabilmek amacı ile o kısımlar dolu olanları göç hızını hesapladık boş olanları na olarak kabul ettik ve nufus artış hızından doğal artışı çıkarark hesaplayacağımızı belirttik. başka bir deyişle yıl sonu nüfusundaki artış, sadece doğanlar ve ölenler arasındaki farkla (Doğal Artış) açıklanamıyorsa; aradaki bu açıklanamayan fark (bakiye) mecburen Net Göç olmak zorundadır diye kabul ettik. 

NEXT...
göç ü nasıl artış hızını doldurduk?
