# **El Yazısı Alfabe Karakter Tanıma Projesi**
Bu depo, A-Z El Yazısı Karakterler Veri Seti üzerinde CNN ve Transfer Learning (MobileNetV2) yaklaşımlarını karşılaştırarak yüksek doğrulukta bir karakter tanıma çözümü geliştirmek amacıyla yapılmıştır. 

## **Giriş**
Bu proje, görüntü işleme alanında sıkça karşılaşılan el yazısı karakter tanıma (Handwritten Recognition) problemini çözmeyi hedefler. Temel amacımız, 28x28 piksel boyutundaki gri tonlamalı el yazısı görüntülerini kullanarak 26 farklı Türkçe alfabe karakterini (A'dan Z'ye) doğru bir şekilde sınıflandırmaktır.

**Seçilen Veri Seti**: Kaggle'dan alınan "A-Z Handwritten Data".

**Kullanılan Algoritmalar**:

  **Temel Evrişimli Sinir Ağı (CNN)**: İki evrişim katmanı ile sıfırdan oluşturulan derin öğrenme modeli.

  **Transfer Learning**: **MobileNetV2** temel mimarisi kullanılarak küçük görüntülere adapte edilen bir yaklaşım.
Tüm teknik analizler, model mimarileri ve kod anlatımları, notebook dosyalarımdaki "karakter_tanıma_analizi.ipynb" markdown hücreleri içerisinde detaylandırılmıştır.

## **Metrikler**
Projemizde iki farklı model mimarisini ve üç farklı optimizasyon tekniğini karşılaştırdık. Çalışmalarımız sonucunda elde edilen temel bulgular ve bunların yorumlanması aşağıdadır:
**Model Başarımı Karşılaştırması**
Temel CNN'nin doğruluk skorunu {test_accuaracy: .4f} f string'i içinde belirtlimiştir. Temel CNN'nin yorumlamasına geçersek iyi bir performans gösterdi, doğruluğun ve karmaşık olmayan bir modelin göreve uygun olduğunu kanıtladı.

MobilNetV2'nin doğruluk skorunu {test_acc_tl:.4f} f string'i içinde belirtilmiştir. MobilNetV2'nin beklentinin altında kaldığını söyleyebiliriz çünkü Transfer Learning, Temel CNN'den daha yüksek skor vermesi beklenir ama MobilNetV2'nin 32*32'den büyük görüntüler için tasarlanmış olmasından kaynaklanıyor olabilir.

**Optimizasyon Sonuçları**
En iyi performansı veren optimizasyon tekniği, {max(results, key=results.get)} olmuştur.
{max(results, key=results.get)} optimizasyon tekniği Adam, RMSprop gibi optimizatörlerin, SDG'ye göre daha karmaşık gradyan yüzeyinde hızla ve etkili bir şekilde minimuma ulaştığını gösterir. Bu el yazısı gibi seyrek ve değişken veriler için adaptif hız ayarının ne kadar kritik olduğunu kanıtlar.


## **Ekler**

Bu projede ek olarak aşağıdaki çalışmalar gerçekleştirilmiştir:

**Feature Map Görselleştirmesi**
Eğitilmiş cls_deneme modelinin Evrişimli katmanlarından çıkan Feature Maps görselleştirilerek, modelin karakterin hangi kısımlarına odaklandığı ve nasıl soyut özellikler çıkardığı incelenmiştir. Bu, modelin siyah kutu olmaktan çıkarılıp yorumlanmasına olanak tanır.

**Keras Callback Kullanımı**
Model eğitiminde Early Stopping  ve ReduceLROnPlateau gibi callback'ler kullanılarak eğitimin verimliliği ve modelin genelleştirme yeteneği artırılmıştır.

## **Sonuç ve Gelecek Çalışmalar**
Yaptığımız çalışma, el yazısı tanıma görevinde sıfırdan geliştirilen bir CNN'in dahi oldukça güçlü sonuçlar verebileceğini göstermiştir. Optimizasyon seçimi, modelin nihai başarısında önemli bir rol oynamıştır.

**Dinamik Veri Toplama**: Projeye daha fazla çeşitlilik katmak için, kullanıcılardan yeni el yazısı örnekleri toplayan bir mekanizma (basit bir web formu) eklemek ve modeli sürekli eğitmek.


# **LİNKLER**
Kaggle Veri Seti Linki: https://www.kaggle.com/code/mahmutyldrmm/mahmut-yildirim-dl-bootcamp-101-proje
