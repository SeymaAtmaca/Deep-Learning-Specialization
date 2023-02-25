<hr>

* Kaynak : 
Bu not, DeepLearning.ai tarafından verilen "Neural Networks and Deep Learning" adlı eğtiime ait notları içermektedir.
İlgili notlar, [sayfasında](https://github.com/quanghuy0497/Deep-Learning-Specialization/tree/main/Course%201%20-%20Neural%20Network%20and%20Deep%20Learning) yer alan İngilizce metinden çevirilmiştir. <br>

<hr>


İçerik : <br>
1) Derin öğrenmeye giriş
    * Bir (Sinir Ağı) SA nedir?
    * Sinir ağlarıyla denetimli öğrenme
    * Neden derin öğrenme yükseliyor?
2) Sinir Ağları Temelleri
    * İkili sınıflandırma
    * Lojistik regresyon
    * Lojistik regresyon maliyet fonksiyonu
    * Gradyan inişi
    * Türevler
    * Daha Fazla Türev Örnekleri
    * Hesaplama grafiği
    * Hesaplama Grafiği ile Türevler
    * Lojistik Regresyon Gradyan İnişi
    * m Örnekleri için Gradyan İnişi
    * Vektörleştirme
    * Lojistik Regresyonu Vektörleştirme
    * Python ve NumPy Hakkında Notlar
    * Genel Notlar
3) Sığ Sinir Ağları
    * Sinir Ağları Genel Bakış
    * Sinir Ağı Temsili
    * Bir Sinir Ağı'nın Çıktısının Hesaplanması
    * Birden fazla örnekte vektörleştirme
    * Aktivasyon fonksiyonları
    * Neden doğrusal olmayan aktivasyon fonksiyonlarına ihtiyaç var?
    * Aktivasyon fonksiyonlarının türevleri
    * Sinir Ağları için Gradyan İnişi
    * Rastgele Başlatma
4) Derin Sinir Ağları
    * Derin L-katmanlı sinir ağı
    * Derin bir Ağda İleri Yayılım
    * Matris boyutlarını doğru şekilde almak
    * Neden derin temsiller?
    * Derin sinir ağlarının yapı taşları
    * İleri ve Geri Yayılım
    * Parametreler vs Hiperparametreler


<br> <br>
<hr>


* Yapay sinir ağları nedir ( What is Neural Network ( NN )) ? 
    - Tek nöron == aktivasyon uygulanmamış lineer regresyona eşittir. (perceptron)
    - Temel olarak tek nöron, girdinin ağırlıkları toplamını ( W^T * X ) hesaplar ve sonra bir eşik değerine göre çıktı tahmin edilir. 
    - Eğer girdiye ait ağırlıklar toplamı eşik değeri geçerse, perceptron çalışır, aksi durumda tahmin yapılmaz.
    - Perceptron, gerçek bir input değeri veya boolean değeri alabilir. Ağırlıklar toplamı ( W^T * X ) değeri 0 ise perceptron 0 çıktısı üretir.
    - Perceptron’ un dezavantajı, yalnızca binary çıktılar sağlamasıdır. Perceptron’ larda ağırlık ve bias üzerinde yapılan küçük değişiklikler perceptron çıktısını etkiler. Bu noktada sigmoid fonksiyonu kullanılabilir. Örneğin sigmoid ile yapılan bir değişiklik perceptron = 0 çıktısını 1’ e çevirebilir. Burada asıl çıktı 0.7’ dir ancak yuvarlama işlemi sonucu, çıktı değeri 1 olarak elde edilir. Sigmoid uygulanmış perceptron, lojistik regresyon gibi davranır. 
    - Basit bir sinir ağı yapısı aşağıda verilmiştir.<br><br>
    -
![1.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/1)%20Neural%20Networks%20and%20Deep%20Learning/images/1.jpg)





















