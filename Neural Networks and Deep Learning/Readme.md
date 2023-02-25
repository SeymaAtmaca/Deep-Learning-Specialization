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
    
![1.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/1.jpg)<br><br>
    - ReLU, en popüler aktivasyon fonksiyonlarındandır. Derin sinir ağlarının daha hızlı eğitilmesini sağlayan bir aktivasyon fonksiyonu çeşididir.
    - Sinir ağlarında gizli katmanlar, girişler arası bağlantıları otomatik olarak tahmin eder.

<br><br>
![2.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/2.jpg)<br><br>
* Sinir Ağlarında Denetimli Öğrenme ( Supervised Learning ) : 
    - Denetimli öğrenme için farklı sinir ağları mevcuttur : 
        * CNN ( evrişimli sinir ağları ) | Bilgisayarlı görüde kullanılır.
        * RNN (Tekrarlayan Sinir Ağları ) | Konuşma tanıma veya NLP’ lerde kullanılır.
        * Standart sinir ağları ( Yapılandırılmış veriler için kullanılır. )
        * Karma - özel sinir ağları 
    - Yapılandırılmış veriler veritabanları ve tablolara benzer. Bunlar görüntü, video, ses ve metin olabilir.

* Derin Öğrenme Neden Yükselişte ? : 
    1. Data : 
<br><br>
![3.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/3.jpg)<br><br>
        - Küçük veriler için SVM’ ler ve lineer regresyon kullanılabilir.
        - Büyük veriler üzerinde sinir ağları, SVM’ lerden daha kullanışlıdır.
        - Büyük veri için büyük NN ( sinir ağı ), orta boyutlarda bir NN’ den daha iyidir. 
        - Günümüzde kullanılan telefonlar, IoT cihazlar düşünüldüğünde veri oldukça fazladır.
    2. Çalışma Yöntemleri : 
        - GPU’ lar,
        - Güçlü CPU’ lar,
        - Dağıtık hesaplama ( Distributed computing ),
        - ASIC
    3. Algoritma : 
        - Ortaya çıkan yeni algoritmalar, NN’ lerin çalışma yöntemlerini oldukça etkilemiştir. Örneğin, bir sinir ağında ReLU kullanımı, sigmoid’ e göre daha işlevseldir. 

<b>SİNİR AĞI  (NN )TEMELLERİ : <b><br>
* İkili Sınıflandırma | Binary Classification : 
    - Binary classification kullanımında lojistik regresyon mantığı ele alınır.
<br><br>
![4.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/4.jpg)<br><br>

    - Mevcut bir görüntüde kedi olup olmadığı problemi ele alınsın:
        * M, eğitim vektörlerinin sayısıdır
        * Nx giriş vektörünün boyutudur
        * Ny çıktı vektörünün boyutudur
        * X(1) birinci giriş vektörüdür
        * Y(1) birinci çıkış vektörüdür
        * X = [x(1) x(2).. x(M)]
        *  Y = (y(1) y(2).. y(M))
    - ( Bu dersin devamının kurs içeriğinden takip edilmesi daha verimli olur. İligili ders linki : https://www.coursera.org/lecture/neural-networks-deep-learning/binary-classification-Z8j0R )

* Lojistik regresyon : 
    - Lojistik regresyon, ikili sınıflandırma için kullanılır. 
    - Denklem : 
        * y = wx + b
        * Eğer x bir vektör ise : y = W^T * X + b
        * Y’ nin 0-1 arasında olması gerekiyorsa : y = sigmoid(W^T * X + b)
    - Yukarıda verilen son denklemde, W Nx’ in bir vektörüdür ve b gerçel bir sayıyı ifade etmektedir.
    - İkili sınıflandırma problemlerinde y’ nin 0-1 arasında olması gerekmektedir.

* Lojistik regresyon maliyet fonksiyonu : 
    - Maliyet fonksiyonu, tüm eğitim örneklerinin loss fonksiyonlarının ortalamasını hesaplamaktadır.
    - Loss fonksiyonu olarak karekök hatası ele alınsın ( square root error ) : 
        * L(y',y) = 1/2 (y' - y)^2
    - Bu loss fonksiyonu, algortimayı yerel olmayan minimum noktalarına taşıyacağı için elverişli değildir. 
    - Bunun yerine kullanılacak loss fonksiyonu : 
        * L(y',y) = - (y*log(y') + (1-y)*log(1-y'))
    - Bu loss fonksiyonunda eğer y= 1 ise  y' için en büyük değer olan 1 sonucunun alınması istenir. y = 0 ise y' için mümkün olan en küçük değer yani 0 alınması beklenir. 
    - Loss fonksiyonundan hareketle maliyet fonksiyonu şu şekildedir : 
        * J(w,b) = (1/m) * Sum(L(y'[i],y[i]))
    - Loss, tek eğitim örneği için hatayı hesaplarken, maliyet fonksiyonu tüm eğitim seti için kayıp fonksiyonlarının ortalamasını ele alır. 

* Gradient Descent : 
    - Maliyet fonksiyonunu minimize eden w ve b değerlerinin tahmin edilmesi beklenmektedir. 
    - Önce w ve b 0 ile başlatılır. Daha sonra elde edilen değerler üzerinde minimuma yaklaşmak için iyileştirmeler yapılır. 
    - Gradient descent algoritması : w= w -alfa * dw formülü ile tekrar eder. Burada kullanılan alfa değeri öğrenme oranı ( learning rate ) ve dw ise w’ nin türevidir. 
    - Formülde dw yani türev kullanılmasının sebebi, parametre iyileştirmede bir yön oluşturmaktır. 
    - Buradan hareketle kullanılan asıl iki denklem : 
        * w = w - alpha * d(J(w,b) / dw) # Fonksiyonun w yönündeki eğimi
        * b = b - alpha * d(J(w,b) / db) # Fonksiyonun b yönündeki eğimi 

* Türevler ( Derivatives ) : 
    - Bu derste bazı türev alma örnekleri verilmiş. 
    - Türev dersleri için https://www.youtube.com/watch?v=-AA0CtP-8rE&list=PL4X0pEzmVyOE-7bVBuGhLHYBEekjkLunl videolarını inceleyebilirsiniz
* Hesaplama Grafı : 
    - Soldan sağa doğru bir hesaplama örneği yapacak olursak, graf şu şekilde gözükecektir :
<br><br>
![5.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/5.jpg)<br><br>

  
  
  
  
<br><br>
![6.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/6.jpg)<br><br>

<br><br>
![7.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/7.jpg)<br><br>

<br><br>
![8.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/8.jpg)<br><br>

<br><br>
![9.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/9.jpg)<br><br>

<br><br>
![10.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/10.jpg)<br><br>

<br><br>
![11.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/11.jpg)<br><br>

<br><br>
![12.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/12.jpg)<br><br>

<br><br>
![13.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/13.jpg)<br><br>

<br><br>
![14.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/14.jpg)<br><br>





















