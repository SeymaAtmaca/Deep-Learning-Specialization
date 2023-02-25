## Kaynak :book: : 
Bu not, DeepLearning.ai tarafından verilen "Neural Networks and Deep Learning" adlı eğtiime ait notları içermektedir.
İlgili notlar, [sayfasında](https://github.com/quanghuy0497/Deep-Learning-Specialization/tree/main/Course%201%20-%20Neural%20Network%20and%20Deep%20Learning) yer alan İngilizce metinden çevirilmiştir. <br>

<br>

## İçerik : :point_down: <br>

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
    - Basit bir sinir ağı yapısı aşağıda verilmiştir.
<br><br>   
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
* Hesaplama Graflarında Türev Kullanımı : 
      - x -> y -> z  için türevdeki zincir kuralı şu şekildedir : d(z)/d(x) = d(z)/d(y) * d(y)/d(x)
      - Graf görünümü ise :
<br><br>
![6.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/6.jpg)<br><br>
* Lojistik regresyon Gradyan İniş ( Logistic Regression Gradient Descent ) : 
      - Derste gradyan descent’ in lojistik regresyon üzerinde kullanımı anlatılmıştır. 
<br><br>
![7.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/7.jpg)<br><br>
      - dersin video üzerinde tekrarı daha verimli olacaktır. Derse ait video linki : https://youtu.be/z_xiwjEdAC4 

* m örnek için Gradient Descent : 
      - Sahip olunan değerler : 
               - X1                  Feature
               - X2                  Feature
               - W1                  Weight of the first feature.
               - W2                  Weight of the second feature.
               - B                   Logistic Regression parameter.
               - M                   Number of training examples
               - Y(i)                Expected output of i
      - Bu değerler üzerinde z ağırlığı ve loss değeri uygulanırsa : 
<br><br>
![8.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/8.jpg)<br><br>

      - Yukarıdaki fonksiyonlar üzerinde türev uygulandığında ise :
               - d(a)  = d(l)/d(a) = -(y/a) + ((1-y)/(1-a))
               - d(z)  = d(l)/d(z) = a - y
               - d(W1) = X1 * d(z)
               - d(W2) = X2 * d(z)
               - d(B)  = d(z)
               
               
  Bu fonksiyonlar için sözde kod :
<br><br>
![9.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/9.jpg)<br><br>

   Yukarıdaki kod, hatayı en aza indirmek için birkaç tekrar ile çalıştırılmalıdır. Dolayısıyla, lojistik regresyonu uygulamak için iki iç döngü olacaktır. <br>
   Vektörleştirme, döngüleri azaltmak için derin öğrenmede çok önemlidir. Son kodda, vektörleştirmeyi kullanarak tüm döngüyü tek adımda yapabiliriz!

* Vektörleştirme : 
   - For döngülerinden kurtulabilmek için vektörleştirme kullanılır. 
   - Bunun için genelde Numpy kullanılır. ( https://numpy.org/doc/stable/) 
* Lojistik regresyonu vektörleştirme : 
   - Elimizde bir X matrisi, X’ e ait [Nx, m] , Y ve Y’ ye ait [Ny, m ] matrisi olsun.
   - Ağırlıkalr üzerinde [Z1, Z2, … Zm ] = W’ * X + [ b,b,b,b..b ] şeklinde yapılan hesaplama, Python’ da şu şekilde uygulanmaktadır : 
      * Z = np.dot(W.T, X) + b  # Z.shape = (1, m)
      * A = 1 / 1 + np.exp(-Z) # A.shape = (1, m ) 
   - Lojistik regresyonda gradyan inişi ( gradient descent) vektörleştirme :  
      * dz = A - Y     # dz.shape = (1,m)
      * dw = np.dot(X, dz.T) / m    # dw.shape = (Nx, 1)
      * db = dz.sum() / m   # sb.shape = (1,1)


* Python ve Numpy ile ilgili notlar : 
   - Numpy’ da : 
      * obj.sum(axis = 0 )   # sütunları toplar
      * obj.sum(axis = 1 )   # satırları toplar
   - Basit bir sigmoid işlemi : 
	   * s = sigmoid(x)
	   * ds = s * (1 - s)       # derivative  using calculus
   - Bir görüntüyü düzleştirirken şu şekilde yeniden boyutlandırma yapılabilir : 
      - v = image.reshape(image.shape[0]*image.shape[1]*image.shape[2],1)  


<br>

* Genel Notlar : 
   - Bir sinir ağını oluşturmak için genel adımlar şunlardır : 
      1.Model yapısı tanımlanır ( giriş özellikleri, çıktı sayısı gibi),
      2.Modelin parametreleri başlatılır.
      3.Döngü : 
         * loss hesabı ( ileri yayılım),
         * Gradyan hesabı ( geri yayılım ) ,
         * Parametrelerin güncellenmesi (gradyan iniş ),
      4.Veri setinin ön işlemesi önemlidir,
      5.Hiperparametre ayarları önemlidir ( öğrenme oranı gibi ),

<b>Shallow Neural Networks : <b>
* Neural Networks Overview : 
   - Lojistik regresyonda : <br>
      X1  \  <br>
      X2   ==>  z = XW + B ==> a = Sigmoid(z) ==> l(a,Y) <br>
      X3  / <br> <br>
   - Sinir ağlarının bir katmanında :  <br>
      X1  \   <br>
      X2   =>  z1 = XW1 + B1 => a1 = Sigmoid(z1) => z2 = a1W2 + B2 => a2 = Sigmoid(z2) => l(a2,Y) <br>
      X3  / <br> <br>
   - X = (X1, X2, X3 …) şeklinde bir girdi vektörünü ve Y (1 x 1 ) boyutlarında bir çıkışı ifade etmektedir.

* Sinir Ağı Temsili : 
   - NN, girdi, gizli ve çıktı katmanlarından oluşmaktadır.
   - a0 = x ( giriş katmanı ) ,
   - a1 = gizli nöronların aktivasyonu,
   - a2 = çıktı katmanı

* Sinir Ağı çıktılarının Hesaplanması : 
   - Gizli katmanlara ait hesap : 
<br><br>
![10.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/10.jpg)<br><br>



   - Yukarıdaki görsele ait bilgiler aşağıda verilmiştir : 
      * noOfHiddenNeurons = 4
      * Nx = 3
      * Değişkenlerin şekilleri:
         - W1 birinci gizli katmanın matrisidir, (noOfHiddenNeurons,nx) şeklindedir.
         - b1 birinci gizli katmanın matrisidir, (noOfHiddenNeurons,1) şeklindedir.
         - z1, z1 = W1*X + b denkleminin sonucudur, (noOfHiddenNeurons,1) şeklindedir
         - a1, a1 = sigmoid(z1) denkleminin sonucudur, (noOfHiddenNeurons,1) şeklindedir
         - W2, ikinci gizli katmanın matrisidir, (1,noOfHiddenNeurons) şeklindedir.
         - b2 ikinci gizli katmanın matrisidir, (1,1) şeklindedir.
         - z2, z2 = W2*a1 + b denkleminin sonucudur, (1,1) şeklindedir
         - a2, a2 = sigmoid(z2) denkleminin sonucudur, (1,1) şeklindedir

* Birkaç vektörleştirme örneği : 
   - 2 katmanlı sinir ağı için ileri yayılım : 
        * for i = 1 to m
        * z[1, i] = W1*x[i] + b1      # shape of z[1, i] is (noOfHiddenNeurons,1)
        * a[1, i] = sigmoid(z[1, i])  # shape of a[1, i] is (noOfHiddenNeurons,1)
        * z[2, i] = W2*a[1, i] + b2   # shape of z[2, i] is (1,1)
        * a[2, i] = sigmoid(z[2, i])  # shape of a[2, i] is (1,1) <br>
   - Formülsel gösterim : 
        * Z1 = W1X + b1     # shape of Z1 (noOfHiddenNeurons,m)
        * A1 = sigmoid(Z1)  # shape of A1 (noOfHiddenNeurons,m)
        * Z2 = W2A1 + b2    # shape of Z2 is (1,m)
        * A2 = sigmoid(Z2)  # shape of A2 is (1,m)
   - Yukarıda verilen m ifadesi sütun sayısını ifade etmektedir.

   - Verilen örnekte X = A0 denilebilir. Bu haliyle tekrar yazarsak : 
        * Z1 = W1A0 + b1    # shape of Z1 (noOfHiddenNeurons,m)
        * A1 = sigmoid(Z1)  # shape of A1 (noOfHiddenNeurons,m)
        * Z2 = W2A1 + b2    # shape of Z2 is (1,m)
        * A2 = sigmoid(Z2)  # shape of A2 is (1,m)

* Aktivasyon Fonksiyonları : 
   - Sigmoid : A = 1 / (1 + np.exp(-z)) # Z, giriş matrisidir. Sigmoid değeri [0-1] aralığındadır.
   - TanH : A = (np.exp(z) - np.exp(-z)) / (np.exp(z) + np.exp(-z)) # A = np.tanh(z) şeklinde de kullanılabilir. TanH değeri [-1, 1] aralığındadır. 
   - Sigmoid ve TanH’ de genel olarak ortak sorun, giriş çok küçük veya çok büyük olduğu durumlaarda eğimin sıfıra yakınsaması ve gradyan üzerinde problemlere yol açmasıdır.
   - Sigmoid ve TanH probleminin gradyanlar üzerindeki bu probleminin çözülebilmesi için ReLu kullanılmaktadır.
   - ReLU : RELU = max(0,z) # yani z negatifse eğim 0'dır, z pozitifse eğim doğrusal kalır.
   - Sınıflandırma için şu şekilde bir seçim yapılabilir :  0 ile 1 arasındaysa, çıkış aktivasyonunu sigmoid, değilse RELU olarak kullanılabilir.
   - RELU'dan farklı olarak Leaky RELU aktivasyon fonksiyonu, girişlerin negatif olduğu durumlar için de kullanılmaktadır.
   - Leaky_RELU = max(0.01z,z) 
   - Sinir ağlarında genel olarak şu değerlere karar verilmesi gerekmektedir : 
      * Gizli katman sayısı.
      * Her gizli katmandaki nöron sayısı.
      * Öğrenme oranı. (En önemli parametre)
      * Etkinleştirme işlevleri.

* Doğrusal Olmayan Aktivasyon Fonksiyonlarına Neden İhtiyacımız Var ? 
   - Doğrusal aktivasyon fonksiyonlarının kullanıldığı durumlarda, eklenen gizli katman her ne olursa olsun çıktı lojistik regresyon gibi doğrusal olur. 

* Aktivasyon Fonksiyonlarının Türevleri : 
   - Sigmoid’ in türevlenmesi : 
      * g(z)  = 1 / (1 + np.exp(-z))
      * g'(z) = (1 / (1 + np.exp(-z))) * (1 - (1 / (1 + np.exp(-z))))
      * g'(z) = g(z) * (1 - g(z))
   - TanH’ nin türevlenmesi : 
      * g(z)  = (e^z - e^-z) / (e^z + e^-z)
      * g'(z) = 1 - np.tanh(z)^2 = 1 - g(z)^2
   - ReLU türevlenmesi : 
      * g(z)  = np.maximum(0,z)
      * g'(z) = { 0  if z < 0 <br>
                  1  if z >= 0  }

   - Leaky ReLU : 
      * g(z)  = np.maximum(0.01 * z, z)
      * g'(z) = { 0.01  if z < 0 <br>
                  1     if z >= 0   }


* Yapay Sinir Ağları için Gradyan İniş ( Gradient Descent ) : 
   - Bu bölümde sinir ağının geriye yayılımı yapılmıştır. <br> 
   - Gradient descent algoritması : <br> 
      * NN parametreleri:
      * n[0] = Nx
      * n[1] = Gizli Nöron Sayısı
      * n[2] = NoOfOutputNeurons = 1
      * W1 şekli (n[1],n[0])
      * b1 şekli (n[1],1)
      * W2 şekli (n[2],n[1])
      * b2 şekli (n[2],1)
   - Maliyet fonksiyonu I = I(W1, b1, W2, b2) = (1/m) * Sum(L(Y,A2))<br> 
   - Gradyan iniş ( Gradient descent ) : 
      * Repeat:
         - Compute predictions (y'[i], i = 0,...m)
         - Get derivatives: dW1, db1, dW2, db2
         - Update: W1 = W1 - LearningRate * dW1
            * b1 = b1 - LearningRate * db1
            * W2 = W2 - LearningRate * dW2
            * b2 = b2 - LearningRate * db2   <br> 
   - İleri yayılım : 
      * Z1 = W1A0 + b1    # A0 is X
      * A1 = g1(Z1)
      * Z2 = W2A1 + b2
      * A2 = Sigmoid(Z2)   <br>    
   - Geri yayılım : 
      * dZ2 = A2 - Y      # Burada eleman bazlı çarpım yapılmaktadır.
      * dW2 = (dZ2 * A1.T) / m
      * db2 = Sum(dZ2) / m
      * dZ1 = (W2.T * dZ2) * g'1(Z1)  # element wise product (*)
      * dW1 = (dZ1 * A0.T) / m   # A0 = X
      * db1 = Sum(dZ1) / m   <br> 
   - Geri yayılım denklemleri aşağıdaki şekilde üretilmiştir :

<br><br>
![11.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/11.jpg)<br><br>


* Rastgele Başlatma : 
   - Lojistik regresyonda ağırlıkları rastgele başlatmak önemli değildi, oysa NN'de onları rastgele başlatmak zorundayız.
   - NN'de tüm ağırlıkları sıfırlarla başlatırsak işe yaramaz (bias’ lar sıfır ile başlatılabilir ):
      * Tüm gizli birimler tamamen aynı (simetrik) olacaktır - tam olarak aynı şey hesaplanır.
      * Her gardyan iniş yinelemesinde, tüm gizli birimler her zaman için aynı şekilde güncellenir.
   - Bunu çözmek için W'ler küçük rastgele sayılarla başlatılır.
      * W1 = np.random.randn((2,2)) * 0.01    # 0.01 yeterince küçük bir sayı döndürür.
      * b1 = np.zeros((2,1))                  # bias’ lar sıfır olabilmektedir. 

<br>

DEEP NEURAL NETWORKS :  <br>
* Deep L-katmanlı Sinir Ağı ( Neural Network ): 
   - Sığ NN ( Shallow NN ), bir veya iki katmanlı bir NN'dir.
   - Deep NN, üç veya daha fazla katmana sahip bir NN'lerdir.
   - Bir NN'deki katman sayısını belirtmek için L gösterimini kullanılacaktır.
   - n[l], belirli bir l katmanındaki nöronların sayısıdır.
   - n[0] nöron giriş katmanı sayısını belirtir. n[L], çıkış katmanındaki nöron sayısını gösterir.
   - g[l] aktivasyon fonksiyonudur.
      * a[l] = g[l] (z[l])
   - w[l] ağırlıkları z[l] için kullanılır
   - x = a[0], a[l] = y'
   - Bunlar, derin sinir ağı için kullanacağımız notasyonlardır.
   - n ve g boyutları aşağıdaki gibidir : 
      * n vektörünün boyutu (1, NoOfLayers+1)
      * g vektörünün boyutu (1, NoOfLayers)
      * Önceki ve geçerli katmandaki nöron sayısına bağlı olarak w’ nin boyutu değişmektedir.
      * Geçerli katmandaki nöron sayısına bağlı olarak b’ nin boyutu değişmektedir.

<br>

* Deep Network’ lerde İleri Yayılım : 
   - Bir giriş için genel ileri yayılım kuralı : 
      * z[l] = W[l] a[l-1] + b[l]
      * a[l] = g[l] (z[l])
   - m input için genel ileri yayılım kuralı : 
      * Z[l] = W[l] A[l-1] + B[l]
      * A[l] = g[l] (Z[l])
   - Tüm katmanların ileri yayılımını bir for döngüsü olmadan hesaplanamaz. BU nedenle bir for döngüsü kullanılması gerekmektedir.
   - Matrislerin boyutları önemli bir sorundur.

<br>

* Matrisleri Doğru Boyutlara Getirme
   - Matrislerde hata ayıklamanın en kolay yolu kağıt-kalem kullanımıdır.
   - W'nin boyutu (n[l],n[l-1])'dir. Sağdan sola düşünülebilir.
   - b'nin boyutu (n[l],1) şeklindedir.
   - dw, W ile aynı şekle sahipken db, b ile aynı şekle sahiptir
   - Z[l], A[l], dZ[l] ve dA[l]'nin boyutları (n[l],m)'dir

<br>

* Neden derin temsiller ( representations ) : 
   - Deep NN, verilerle ilişkileri basitten karmaşığa doğru yapar. Her katmanda bir önceki katmanla ilişki kurmaya çalışır. Örneğin:
      * Yüz tanıma uygulaması:
      * Görüntü ==> Kenarlar ==> Yüz parçaları ==> Yüzler ==> istenen yüz
      * Ses tanıma uygulaması:
      * Ses ==> (sss,bb) gibi düşük seviyeli ses özellikleri ==> Fonemler ==> Kelimeler ==> Cümleler
   - Devre teorisi ve derin öğrenme : 

<br><br>
![12.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/12.jpg)<br><br>

* Derin Sinir Ağlarının Yapı Taşları : 
   - I. katman için ileri ve geri yayılım :
   
<br><br>
![13.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/13.jpg) <br><br>

   - Derin NN blokları : 
   
<br><br>
![14.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Neural%20Networks%20and%20Deep%20Learning/images/14.jpg) <br><br>


* İleri ve Geri Yayılım : 
   - I. katmana ait ileri yayılım sözde kodu : 
      * Input  A[l-1]
      * Z[l] = W[l] A[l-1] + b[l]
      * A[l] = g[l] (Z[l])
      * Output A[l], cache(Z[l])
   - I. katman için geri yayılım sözde kodu : 
      * Input da[l], Caches
      * dZ[l] = dA[l] * g'[l] (Z[l])
      * dW[l] = (dZ[l] A[l-1].T) / m
      * db[l] = sum(dZ[l])/m                # Dont forget axis=1, keepdims=True
      * dA[l-1] = w[l].T * dZ[l]            # The multiplication here are a dot product.
      * Output dA[l-1], dW[l], db[l]
   - Sonrasında loss fonksiyonu kullanılıyorsa : 
      * dA[L] = (-(y/a) + ((1-y)/(1-a)))

<br>

* Parametre ve Hiperparametreler : 
   - NN'nin ana parametreleri W ve b'dir.
   - Hiper parametreler (algoritmayı kontrol eden parametreler) şöyledir:
      * Öğrenme oranı.
      * Yineleme sayısı.
      * Gizli katman sayısı L.
      * Gizli birim sayısı
      * Aktivasyon fonksiyonlarının seçimi.
   - Hiper parametrelerin değerlerini kendiniz denemelisiniz.



















