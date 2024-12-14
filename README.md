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

# ANN Modeli: Yapay Sinir Ağı

Artık toplanan verilerle bir ANN modeli oluşturacağız. Bu model, aracın hareketini kontrol etmek için eğitim alacak.

Adımlar:

•	Yeni Script: ANNDrive_sc adında bir script oluşturun ve ANN kontrolündeki ANNKart'a ekleyin.

•	İleri ve Geri Yön Kontrolü: translation ve rotation verilerini kullanarak ANN modelini eğitin. Bu veriler, aracın hızını ve yönünü belirleyecektir.

# Adaptive Learning ve Ağırlık Yönetimi

ANN'nin başarısını iyileştirmek için, öğrenme süreci boyunca ağırlıkları güncelleyeceğiz.

Adımlar:

•	Epoch Başlangıcı: Her epoch başında ağırlıkları kaydedin. Eğer hata iyileşmezse, önceki ağırlıkları kullanarak öğrenme oranını düşürün.

•	Ağırlık Kaydetme: Eğitim sırasında ağırlıkları kaydedin ve dosyaya yazın.

•	Dosyadan Okuma: Eğitim sonunda öğrenilen ağırlıkları dosyadan okuyarak devam edin.

# Veri Setinin Kaydedilmesi ve İncelenmesi

Toplanan verileri kaydedip, gürültüyü azaltarak daha temiz bir veri seti elde edeceğiz.

Adımlar:

•	Veri Kaydetme: Toplanan veriyi dosyaya kaydedin. System.IO kütüphanesini kullanarak CSV formatında veri kaydedebilirsiniz.

•	Veri İnceleme: Veri setinde gereksiz verileri (noise) temizleyin ve sadece önemli verileri saklayın.

# Sonuç ve İyileştirme

Oyun sonunda, ANN modelini kullanarak go-kart aracının daha doğru hareket etmesini sağlamak için modelin başarısını izleyin. Gerekirse, veriyi manuel olarak düzenleyerek iyileştirmeler yapın.

Adımlar:

•	Eğitim Sonrası Değerlendirme: Modelin hata oranını değerlendirin ve gerektiğinde yeniden eğitim uygulayın.

•	Modeli İyileştirme: Kullanıcı verisini Excel'de açarak çelişen verileri düzeltin ve modeli optimize edin.

Yarış oyununda, oyuncu ve ANN kontrollü araçlar arasında veri toplanarak ANN modeli ile otonom sürüş gerçekleştirilmiştir. Modelin eğitim verisi, aracın çevresindeki engellere olan mesafeleri ve araç hareketini içermektedir. Elde edilen model, oyundaki engellere göre doğru hareketleri yapacak şekilde optimize edilmiştir.

![image](https://github.com/user-attachments/assets/03e95b2e-049e-4c83-ac1c-7e5c536f201a)

![image](https://github.com/user-attachments/assets/8fb5e5b2-a19f-4a6f-a566-b901c4d3cc92)

![image](https://github.com/user-attachments/assets/02ff88c3-405d-4fc9-95dc-bd9391deef90)

![image](https://github.com/user-attachments/assets/0d15bc7a-e548-4ab2-b727-917f08bf1a5f)
