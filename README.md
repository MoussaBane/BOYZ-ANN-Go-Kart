# BOYZ-ANN-Go-Kart
Bilgisayar Oyunlarda Yapay Zeka Dersinin Ödevi 8

# Yeni 3D Proje Oluşturma ve Temel Yapı:

İlk olarak, Unity'de yeni bir 3D proje oluşturun. Bu projede sahnede iki go-kart arabası yer alacak: birincisi oyuncu tarafından klavye ile kontrol edilecek, ikincisi ise Yapay Sinir Ağı (ANN) tarafından kontrol edilecek.

Adımlar:

•	Yeni 3D proje oluşturun ve ANNRacing projesini içe aktarın.

•	Starter sahnesini açın.

•	Sahne Elemanları: İki go-kart aracı sahnede bulunmalı.

•	Araç Hareketi:

Klavye ile Hareket: İlk araç (Kart) için klavye kontrolü eklenir. Bu, araç hareketini sağlamak için klavye tuşlarını kullanmanızı sağlar.
ANN ile Hareket: İkinci araç (ANNKart), ANN tarafından kontrol edilecek.

# Script Oluşturma ve Araba Kontrolü

Yeni bir script oluşturun ve bu script'i ilk araca ekleyin. Bu script, oyuncu tarafından kontrol edilen aracın hareketini sağlayacak.

Adımlar:

•	Yeni Script: Drive_sc adında bir script oluşturun ve bu script'i Kart’a ekleyin.

•	Kaydedin ve Çalıştırın: Script'i kaydedin ve çalıştırarak aracın hareket ettiğinden emin olun.

# Veri Toplama ve Mesafe Hesaplamaları

Yarış sırasında aracın hareket verilerini toplayarak ANN modeli için eğitim verisi oluşturacağız.

Adımlar:

•	Veri Toplama: Aracın her hareketi sırasında translation ve rotation verilerini toplanır.

•	Mesafe Hesaplamaları: Çeşitli yönlerde ışınlar göndererek çevredeki engellere olan mesafeyi ölçülür. Bu mesafeler, ANN'ye girdi olarak sağlanacaktır:

İleri Mesafe: Aracın önüne bir ışın gönderilir.

Sağ ve Sol Mesafe: Araç sağ ve sol yönlere ışınlar göndererek mesafeyi ölçülür.

Çapraz Mesafeler: Sağ ve sol ileri 45 derecelik açılarda ışın gönderilir.

Script için Değişkenler:

•	visibleDistance: Aracın etrafında ışın gönderme mesafesini belirleyecek değişken.

•	Mesafe Değişkenleri: fDist, rDist, lDist, r45Dist, l45Dist gibi mesafe değişkenleri kullanarak çevredeki engellere olan mesafeyi hesaplanır.

# Veri Setinin Düzenlenmesi ve Normalizasyon

Toplanan veri seti ham olacak ve gürültü içerecektir. Bu gürültüyü azaltarak veriyi daha temiz hale getireceğiz.

Adımlar:

•	Gürültü Azaltma: Toplanan veriyi yuvarlayarak yalnızca yeni verilerin listeye eklenmesini sağlar.

•	Normalizasyon: Mesafeleri normalize ederek 0 ile 1 arasında bir değer elde edilir. Bu, verilerin daha uyumlu olmasını sağlar. Normalizasyon için mesafeyi visibleDistance ile bölünür.

•	Değer Tersine Çevirme: Engellere yakınlaştıkça değerlerin artmasını sağlamak için mesafe değerlerini tersine çevirilir.
