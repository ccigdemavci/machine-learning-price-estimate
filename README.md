Makine Öğrenmesi Projesi: Veri Kazıma ve Model Uygulama
Bu proje, çeşitli makine öğrenmesi algoritmalarını kullanarak veri kazıma (web scraping) yöntemleri ile elde edilen verilerin işlenmesini, analize edilmesini ve uygun modellerle sınıflandırma ya da tahmin yapılmasını hedeflemektedir. Veriler üzerinde yapılan analizler, sonuçların değerlendirilmesi ve yorumlanması bu projenin ana hedeflerini oluşturur.

Proje İçeriği
Veri Kazıma (Web Scraping)

İnternetten veri kazıma işlemi, veri kaynağının doğruluğu ve anlamlılığı göz önünde bulundurularak yapılmıştır. Kullanılacak veri kaynağının seçiminde, daha önce analiz yapılmamış bir kaynak tercih edilmiştir.
Elde edilen veri, ürün açıklamaları, fiyatlar, yorumlar, puanlar ve kargo bilgilerini içermektedir. Bu veriler, daha sonra veri analizi ve makine öğrenmesi süreçlerinde kullanılacaktır.
Veri Temizleme ve Hazırlama

Elde edilen veriler, veri analizi yapılmadan önce temizlenmiştir. Eksik ve hatalı veriler düzenlenmiş, sayısal veriler (fiyat, puan, favori sayısı vb.) uygun formatlara dönüştürülmüştür.
Verilerin normalize edilmesi ve eksik değerlerin doldurulması, bu aşamanın önemli bir parçasıdır. Ayrıca, veri setinin anlaşılabilirliği için gereksiz sütunlar temizlenmiştir.
Makine Öğrenmesi Modelleri

Veri setinin doğruluğu artırıldıktan sonra, farklı makine öğrenmesi algoritmaları kullanılarak tahminler ve sınıflandırmalar yapılmıştır.
Linear Regression (Doğrusal Regresyon): Fiyat tahminini yapmak için doğrusal regresyon modeli kullanılmıştır.
Random Forest: Verilerin daha karmaşık ilişkilerini öğrenebilen bir modeldir. Bu model, tahminlerin doğruluğunu artırmaya yöneliktir.
Gradient Boosting: Gradient Boosting, her adımda hataları düzeltmeye çalışan bir algoritmadır ve yüksek doğruluk sağlar.
K-Nearest Neighbors (KNN): Komşu algoritmasıyla, verilerin sınıflandırılmasında kullanılan bir diğer yöntemdir.
Support Vector Regression (SVR): Fiyat tahmininde kullanılan diğer önemli bir regresyon algoritmasıdır.
Optimizasyon

Modellerin doğruluğunu artırmak amacıyla Optuna kütüphanesi kullanılarak hiperparametre optimizasyonu yapılmıştır. Bu, her modelin daha iyi tahminler yapabilmesi için parametrelerin en iyi şekilde ayarlanmasını sağlar.
Sonuçların Değerlendirilmesi

Elde edilen sonuçlar, her modelin doğruluk, hata oranları (MAE, RMSE, R²) ile değerlendirilmiştir.
Modellerin karşılaştırılması yapılmış, hangi modelin daha iyi performans gösterdiği belirlenmiştir.
Görselleştirmeler ile model performansları ve ilişkiler detaylandırılmıştır.

Proje Adımları
1. Veri Kazıma (Web Scraping)
İlk adım olarak, projede kullanacağımız veriyi internetten kazıdık. Bunun için, Trendyol'un kadın çanta kategorisini seçtik çünkü burada çok sayıda ürün ve bu ürünlere ait fiyat, puan, açıklama gibi veriler mevcut. Bu veriler, fiyat tahminleri yapmak için çok anlamlı olacaktır.

Veri Kaynağının Seçimi: Trendyol, popüler ve geniş ürün yelpazesi sunan bir platform olduğundan, burada ürünler hakkında detaylı bilgilere ulaşmak mümkün. Bu nedenle, Trendyol'dan kadın çantalarının verilerini topladık.

HTML Yapısının İncelenmesi: Verileri kazıyabilmek için önce siteyi inceledik. Ürün başlıkları, fiyatları, puanları ve açıklamaları gibi bilgilerin hangi HTML etiketlerinde yer aldığını belirledik. Bu, veri kazıma sürecini doğru yapabilmemiz için çok önemliydi.

Veri Kazıma Süreci: requests kütüphanesiyle siteye istek gönderip, gelen yanıtı BeautifulSoup kullanarak işledik. Her ürünün başlığı, fiyatı, marka adı gibi bilgilerini bu yöntemle çektik.

Veri Toplama ve Kaydetme: Ürün bilgilerini topladıktan sonra, bu verileri CSV formatında sakladık. Sayfaların tümünü kazıyabilmek için sayfalama yaparak çok sayıda ürünün bilgilerini topladık.

2. Veri Temizleme ve Hazırlama
Veriyi kazandıktan sonra, bu veriyi makine öğrenmesi modellerine uygun hale getirmemiz gerekti. Veri genellikle eksik, hatalı ya da format açısından düzgün olmuyor. İşte bu aşamada bu sorunları çözdük.

Eksik Verilerle Baş Etme: Web scraping sırasında bazı ürünlerde fiyat, puan ya da açıklama gibi bilgiler eksik olabiliyor. Bu eksik verileri ya ortalama ile doldurduğumuz ya da o ürünleri veri setimizden çıkardık. Bu sayede, eksik veri sorunu çözüldü.

Veri Formatlarının Düzeltilmesi: Çoğu zaman veriler, işlem yapmaya uygun formatta olmuyor. Örneğin, fiyatlar string (metin) formatında geliyordu, bu yüzden bunları sayıya dönüştürdük. Ayrıca kategorik verileri, yani metinlerden oluşan verileri sayısal değerlere dönüştürdük.

Aykırı Değerlerin Tespiti ve Temizlenmesi: Verideki anormal değerler, yani aykırı değerler (örneğin, aşırı yüksek fiyatlar veya sıfır puanlar), modelin doğruluğunu olumsuz etkileyebilir. Bu yüzden aykırı değerleri görselleştirip tespit ettik ve temizledik.

Veri Normalizasyonu: Makine öğrenmesi modelleri için verilerin belirli bir ölçeğe getirilmesi gerekebiliyor. Bu yüzden fiyat gibi sayısal verileri normalize ettik, yani 0 ile 1 arasında bir değere dönüştürdük. Bu, modellerin daha doğru sonuçlar vermesini sağladı.

3. Makine Öğrenmesi Modelleri
Veriyi temizledikten sonra, analiz için üç farklı makine öğrenmesi algoritması uyguladık. Bu algoritmaların her biri, veriden farklı şekilde öğrenir ve tahminler yapar.

Doğrusal Regresyon (Linear Regression):

Bu model, bağımsız değişkenlerin (örneğin, puan, marka, açıklama uzunluğu gibi) bir bağımlı değişken (fiyat) üzerindeki etkisini öğrenir.
Bu model ile, ürünlerin fiyatlarını tahmin etmeye çalıştık. Doğrusal ilişkileri bulmak için kullanışlı bir modeldi. Modelin başarısını R² skoru ve MAE (Mean Absolute Error) gibi metriklerle değerlendirdik.
Random Forest (Rastgele Orman):

Random Forest, çok sayıda karar ağacından oluşan bir modeldir. Her ağaç, veriyi farklı şekilde işler ve sonrasında bu ağaçların sonuçları birleştirilir. Bu model, karmaşık ilişkileri anlamada oldukça başarılıdır.
Bu modeli fiyat tahminlerinde kullandık. Hem kategorik hem de sayısal verilerle iyi sonuçlar elde ettik. Modelin doğruluğunu Mean Squared Error (MSE) ve R² skoru ile ölçtük.
Gradient Boosting:

Gradient Boosting, zayıf öğrenicilerden (decision tree gibi küçük modeller) oluşur ve her adımda bir önceki modelin hatalarını düzeltmeye çalışır. Bu, daha doğru sonuçlar almak için etkili bir yöntemdir.
Bu modeli de fiyat tahmininde kullandık ve sonuçlar oldukça iyiydi. RMSE (Root Mean Squared Error) ve R² skoru metrikleri ile modelin başarısını değerlendirdik.
K-Nearest Neighbors (KNN):

KNN, veri noktalarını birbirine yakın olanlarla karşılaştırarak tahminler yapar. Bu, özellikle benzer ürünlerin fiyatlarını tahmin etmede çok faydalı olabilir.
Bu modeli de fiyat tahmininde kullandık. F1 skoru ve MAE ile modelin doğruluğunu test ettik.
4. Optimizasyon (Hiperparametre Ayarlama)
Makine öğrenmesi modellerinin performansını iyileştirmek için hiperparametre optimizasyonu yaptık. Hiperparametreler, modelin eğitim sürecinde kullanılan ayarlardır ve doğru değerlerle model daha iyi sonuçlar verebilir.

Optuna Kullanımı: Bu işlem için Optuna kütüphanesini kullandık. Optuna, hiperparametrelerin daha verimli bir şekilde ayarlanmasını sağlar. Bu sayede, her modelin parametrelerini test ederek en iyi sonuçları elde ettik.
5. Sonuçların Değerlendirilmesi
Modelin başarılarını değerlendirdik ve sonuçları anlamak için birkaç metrik kullandık:

Model Karşılaştırması: Farklı modelleri karşılaştırarak, en iyi sonucu veren modeli belirledik.
Görselleştirmeler: Modellerin tahminlerini ve doğruluklarını görselleştirdik. Örneğin, doğru tahminlerin ve hatalı tahminlerin görsel olarak nasıl dağıldığını gösteren grafikler oluşturduk.
Sonuç olarak, her bir modelin performansını ölçtük ve en iyi tahminleri yapan modeli belirledik. Proje boyunca öğrendiğimiz yöntemleri kullanarak, veriyi analiz ettik ve makinelerimizin nasıl daha iyi tahminler yapabileceğini gösterdik.

Bu şekilde, her adımı daha anlaşılır ve insana yakın bir dilde yazdım. Umarım faydalı olur! parametre kombinasyonu belirlenmiştir.  
