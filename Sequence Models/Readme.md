
<ul>
  <li>NLP lerde CNN kullanılmama sebepleri :   </li>
  <ul>
    <li >Çıkış farklı boyutlarda olabilir,   </li>
    <li>Farklı konumlarda öğrenilen özellikler paylaşılamaz. (Giriş çıkışta değil, ara katmanlarda öğrenilen özellikler )  Bu nedenle Tekrarlayan sinir ağı RNN kullanılır. Bir RNN örneği  ; </li>
  </ul>
</ul><br>

![1.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/1.jpg) <br>
    
* RNN’ ler genelde sıfır ile başlatılır. Kullanıhlan üç ağırlık matrisi : Wax, Waa, Wya dır. <br>
  - Wax :  ( Gizli nöron sayısı, nx )
  - Waa : ( Gizli nöron sayısı, gizli nöron sayısı ) ,
  - Wya : (ny, gizli nöron sayısı ) 

* Waa , RNN’ in önceki katmanlardan korumaya çalıştığı bellketir.  İLgili RNN mimarisinde y<t> çıkışı, bir önceki giriş ve aktivasyonlara bağlıdır. Yani y<4> çıkışı için hesapları sadece x<1>, x<2> ve x<3> etkiler. x<4> ün etkisi yoktur. 

![2.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/2.jpg) <br>

  
  
* Ancak bu RNN lerde ortayaçıkan sorun, sonraki bilgileri kullanamıyor olmasıdır. Örneğin “Teddy, bir başkandı”  cümlesinde Teddy isminin bir şahıs olduğu sonucuna başkan kelimesi ile varabiliyoruz ancak bu bilgi, ileriki seviyelerden alınamıyor. Bunun çözümü için “Çift Yönlü RNN”  kullanılmaktadır. 
* Mevcut, çift yönlü olmayan RNN ler için ileri besleme denklemleri : 
  
![3.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/3.jpg) <br>
  
* a’ nin aktivasyon fonksiyonu genelde tanh veya ReLU’ dur. Y için ise sigmoid veya softmax kullanılmaktadır. Özel isim- varlık modelinde iki sınıf yer aldığı için sigmoid örneği yapılmıştır. Bu son denklemleri biraz basitleştirerek ele alacak olursak basitleştirilmiş RNN gösterimi ; 

  ![4.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/4.jpg) <br>
  
  - Wa, Waa ve Wax in sıkıştırılmış gösterimidir.
  - Wa shape : ( gizli nöron sayısı, gizli nöron sayısı ) 
  - [a<t-1>, x<t> ] shape : ( gizli nöron sayısı + n_x , 1)
  
* Bonus : Ayrıntılı RNN tek cell görünümü : <br>
  ![5.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/5.jpg) <br>
  
* RNN : <br>
    ![6.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/6.jpg) <br>
  
  
* Zaman içinde geri yayılım : Geri yayılım, ileri yayılım yapıldıktan sonra sistemler tarafından otomatik olarak gerçekleştirilir. Ancak RNN’ lerde ayrıntılı incelenmesi bir artıdır. Geri yayılım grafiği ; <br>
   ![7.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/7.jpg) <br>
  
* Burada Wy, by, Wa, ba her dizi öğesi için ortak kullanılmaktadır. RNN hücresinde genel geri yayılıma bakılacak olunursa ; <br>
  ![8.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/8.jpg) <br>
 
* Burada cross-entropy fonksiyonu kullanılacak olursa ; <br>
  ![9.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/9.jpg) <br>

* Loss ile yayılım akışı : <br>
  ![10.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/10.jpg) <br>
  
  - kırmızı oklar geri yayılımı belirtir. Loss, zaman içindeki geri yayılımdır. <br>
  
* Farklı RNN Türleri :  <br>
  ![11.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/11.jpg) <br>
  - bir müzik üretimi modeli, birden çoğa mimari örneğidir. Üretilen sonuç, ağda geri beslenir ; <br>
  ![12.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/12.jpg) <br>
  - Makine çevirisi modelleri, many-to-many mimarisine örnektir. Kodlayıcı, giriş dizisini bir matrise çevirir ve çıkışları oluşturmak için bunu kod çözücüye besler. Çeviri için örnek bir many-to-many mimarisi ;  <br>
  ![13.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/13.jpg) <br>
  - RNN türlerinin genel özeti ; <br>
  ![14.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/14.jpg) <br>
* Dil Modeli ve Dizi Oluşturma : Bir dil modeli uygulamasında, ses açısından benzer iki cümle arasında bir olasılık değeri üzerinden seçim yapılabilmesi için dil modelelri kullanılıyor. Burada benzer cümleler için verilen örnek : 
  - The apple and pair salad
  - The apple and pear salad
	 Bu örnekte kararın verildiği nokta pair-pear bölümüdür. Dil modeli hangi kelimenin doğru seçenek olduğunu belirtmek için iki kelime adına birer olasılık değeri döndürerek seçim yapılmasını sağlar.Bir dil modelinin işi, verilen herhangi bir sözcük dizisinin olasılığını vermektir.
* RNN’ lerde dil modelleri nasıl oluşturulur ? : 
  - İlk olarak eğitim veri seti için büyük bir hedef dil metni sözlüğü oluşturulmalıdır.
  - Daha sonra bu sözlük üzerinde her kelime teker teker okunarak birer simgeye dönüştürülür. 
  - Cümle sonlarını ifade etmek için <EOS> ve bilinmeyen yeni kelimeler için <UNK> simgesi eklenir. 
* “Kediler günde 15 saat uyurlar. <EOS>”  - ( “Cats average 15 hours of sleep a day. <EOS> “)  cümle örneği üzerinden konu ele alınmıştır.  Eğitim sürecinde ; 
  ![15.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/15.jpg) <br>
  
* Loss için cross-entropy kullanılır ;  <br>
  ![16.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/16.jpg) <br>
  
  Burada i, kelimeleri, t ise zamanı ifade etmektedir. Bu modelin kullanımında ; 
  1) Bir sonraki kelimenin olasılığını tahmin etmek için cümle RNN’ e beslenir. Daha sonra son y^<t> vektörü maksimum olasılığa göre sıralanır. 
  2) Bir cümleye ait genel olasılık hesabında ise aşağıdaki işlem yapılır ; 
    - P(y^<1>, y^<2>, y^<3> ) = P(y^<2> | y^<1> ) * P(y^<1>, y^<2>)
    - Kısaca cümle RNN’ e beslenmiş ve olasılıkları çarpılmış olur.   
* Yeni dizilerin örneklenmesi : 
  - Bir dil modelinin, eğitildikten sonra yeni diziler üzerinde kullanımı aşağıda verilmiştir.
    1) Aşağıdaki model göz önüne alınırsa ; <br> 
    ![17.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/17.jpg) <br>
    2) İlk olarak a^<0> ve x^<1> zeros vektörleri modele gönderilir.
    3) Daha sonra ilk çıktı olan ŷ <1> ile elde edilen dağılımdan rastgele bir tahmin seçilir. Örneğin bu tahmin “The “ olabilir. Numpy üzerinde bu rastgele seçim işlemi “numpy.random.choice() “ ile yapılmaktadır. Bu satır, yeni bir dizi modele uygulandığında, cümlenin ilk kelimesini rastgele seçilmesini sağlar. 
    4) ŷ <2> ‘ nin hesabı için son tahmin edilen kelime olan ŷ <1> ve a <2> değerleri kullanılır. 
    5) <EOS> simgesi gelene kadar bu tahmin işlemleri devam eder. 
![18.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/18.jpg) <br>
 
* Yukarıda anlatılan model, kelime düzeyindedir. Bunun dışında karakter düzeyinde de bir model inşa edilebilir. Bu modellerde sözlük olarak [a,..z,A,...Z, !,?,-,...] vb karakterler kullanılır. Karakter bazında kullanılan modellerin, kelime modellerine göre bazı avantaj ve dezavantajları mevcuttur. 
  - Avantajları : <UNK> içermezler. Çünkü bütün karakterler sözlükte mevcuttur.
  - Dezavantajları : 
    * Daha uzun diziler elde edilir. 
    * Karakter düzeyinde modeller, cümlenin önceki bölümlerinin, sonraki bölümlerini nasıl etkilediğine dair bağımlılıkları yakalamada daha da zorlanır. 
    * Hesaplama açısından daha maliyetlidir, eğitilmesi daha zorludur. 

* RNN’ ler için Vanishing Gradients : 
    - NOT : Kaybolan Gradyan probleminin daha ayrıntılı açıklaması için kolay anlaşılabilir bir site : https://sefiks.com/2018/05/31/an-overview-to-gradient-vanishing-problem/ 
    - Bir örnek üzerinden gidilecek olunursa, aşağıdaki cümleler ele alınsın.
      * The cat, which already ate …, was full”
      * The cats, which already ate …, were full”
    - Bu modelde cat için was ve cats için were kullanılması gerektiği öğrenilmelidir. Yukarıdaki örnekte verilen … , arada bulunan birden fazla kelimeyi ifade etmektedir. Ancak RNN’ ler buradaki gibi uzun vadeli bağımlılıkları yakalamada başarılı değildir. Bu nedenle Vanishing Gradyan problemi, uzun dizi boyutuna sahip RNN’ lerde de ortaya çıkmaktadır. Örnekte “was” hesabı için, geride kalan her değer için gradyanın hesaplanması gerekmektedir. Bu noktada ortaya çıkan kesir çarpımları  gradyanı yok edebilirken, büyük sayıların çarpımı ise gradyanı patlatma ( aşırı büyütme )  eğiliminde olur. Bu, kullanılan ağırlıkların doğru güncellenmesini engeller.
    - Vanishing Gradients : RNN’ lerde , patlayan gradyandan ( exploding gradients ) çok daha fazla soruna sebep olabilmektedir. Bu sorunun çözümü, ilerleyen bölümlerde ele alınacaktır. 
    - Exploding Gradients : Patlayan gradyan çözümünde kullanılan bir yöntem, gradyanın bir eşik değerden fazla olduğu durumlarda degrade kırpma kullanımıdır. Bu noktada, gradyan vektörünün bir kısmı yeniden ölçeklendirilmiş olur. Aşağıda gradyan kırpma için bir örnek verilmiştir. 
  ![19.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/19.jpg) <br>
  
* NOT : 
  1) Exploding Gradyan ( Patlayan Gradyan ) problemi çözümü için yöntemler : 
    - Gradient clipping,
    - Kesilmiş geri yayılım
  2) Vanishing Gradyan ( Kaybolan Gradyan ) problemi için yöntemler : 
    - Ağırlık başlatma 
    - LSTM / GRU ağı kullanımı
    - Echo state networks
* GRU - Gated Recurrent Unit : 
    - GRU, kaybolan gradyan probleminin çözümü için uzun vadeli bağımlılıkların hatırlanmasını sağlayabilen bir RNN türüdür. ( Dersin bu noktasında referans verilen makale linkleri : 
      * https://arxiv.org/abs/1409.1259 
      * https://arxiv.org/abs/1412.3555  ) 
    - Temel RNN birimi :<br> 
    ![20.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/20.jpg) <br>
    - GRU’ larda her katman için atanan ve unutup-unutmama durumunu ifade eden c bellek hücresi değişkeni vardır. c <t> = a <t> dir. GRU’ lara ait denklemler :<br> 
    ![21.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/21.jpg) <br>
  Burada c^<t-1> eski değer ve  c̃ <t> aday değerdir. <br>
    - Update gate ( güncelleme kapısı ) , Gama olarak adlandırılır ve 0 - 1 arasında değer alır. Güncelleme kapısı sayesinde mevcut hafıza hücres, önceki hücreye göre güncellenebilir.<br> 
   ![22.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/22.jpg) <br>
  
    - Dersin bu noktasında kaynak gösterilen link : http://colah.github.io/posts/2015-08-Understanding-LSTMs/ 
    - Daha önce verilen kedi örneğinden ( the cat, which already ate …, was full ) devam edilirse;
      * U’ nun 0-1 olduğunu ve tekil bir kelimenin ezberlenip ezberlenmemesi gerektiğini söyleyen bir bit olduğunu düşünelim.Burada kelimeleri bölüp, C ve U değerlerini teker teker alacak olursak ; <br>
  ![23.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/23.jpg) <br>
      * GRu’ larda, U 0.00001 gibi çok küçük değerlerde olduğu için vanishing gradient problemi yaşanmaz. 
      * Shapes :
        1) a^<t> : ( gizli_nöron_sayısı, 1)
        2) c^<t> : (gizli_nöron_sayısı, 1) 
        3) c~<t> : (gizli_nöron_sayısı, 1) 
        4) u^<t> : (gizli_nöron_sayısı, 1) 
        - NOT : Denklemlerde bulunan çarpma, eleman bazlı çarpmadır. 
        - Bu noktaya kadar açıklanan GRU, Basitleştirilmiş - Simplified GRU’ dur. Buradan sonra Full GRU açıklanacaktır. Full GRU, bir sonraki c tahmini için kullanılır. Bir önceki c değerinin ( c^<t-1> ) , bir sonraki c değerini ( c^<t> ) nasıl etkilediğini, ne derece bağımlı olduğunu açıklamak için kullanılır.  <br>
  ![24.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/24.jpg) <br>
        - Yukarıdaki formülde r_u ( gama_r ), ilgi düzeyini göstermektedir. 
* LSTM ( Uzun Kısa süreli bellek ) :  LSTM, uzun vadeli bağımlılıkları tutabilmek için kullanılan bir RNN türüdür. ( NOT : LSTM için açıklayıcı bir link : https://mfakca.medium.com/lstm-nedir-nas%C4%B1l-%C3%A7al%C4%B1%C5%9F%C4%B1r-326866fd8869 ) GRU’ larda c^<t> = <^<t> iken, LSTM’ lerde c^<t>, a^<t>’ ye eşit değildir. LSTM’ e ait denklemler aşağıda verilmiştir. <br>
   ![25.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/25.jpg) <br> 
        - LSTM’ e ait genel bir yapı ; <br>
  ![26.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/26.jpg) <br>
        - Yukarıdaki bu temel yapı birimleri ise birbirine şu şekilde bağlanmaktadır ; <br>
    ![27.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/27.jpg) <br>
        - Genel olarak bakıldığında GRU’ lar daha basittir ve daha büyük ağların kurulmasında kullanılabilir. Ancak LSTM’ ler daha güçlüdür. LSTM’ e ait hücre geri yayılımı aşağıda verilmiştir. <br>
  ![28.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/28.jpg) <br>
 
* Çift Yönlü RNN ( Bidirectional RNN ) : Dizi modellerini daha güçlü hale getirebilmek için LSTM, GRu dışında kullanılabilecek bir diğer yapılar ise Bidirectional RNN’ ve Deep RNN’ lerdir. <br>
  ![29.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/29.jpg) <br>  
  - Bu örnekte Teddy ismi bear ile çözümlenebilir. Bu noktada algılama probleminin çözülebilmesi için Bidirectional RNN’ ler kullanılır. BiDirectional RNN lerin genel yapısı aşağıda verilmiştir.<br>
     ![30.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/30.jpg) <br>
    - Görüldüğü gibi yapı döngüsel değildir. İleri yayılımın bir kısmı soldan sağa, bir kısmı sağdan sola ilerler. Bu sayede her iki taraftan da öğrenme gerçekleşmiş olur. Tahmin aşamasında hem sol hem de sağdan gelen iki aktivasyon çıktısı da kullanılır ve  ŷ <t> hesaplanır. 
    - Buradaki bloklar, temel RNN’ ler , LSTM’ ler veya GRU’ lar da dahil olmak üzere herhangi bir RNN olabilmektedir.
    - Bidirectional RNN’ lerin dezavantajı ise, işlemek için tüm diziye ihtiyaç duyulmasıdır. Bu da gerçek zamanlı kullanımlarda gecikmelere sebep olabilmektedir.
  
* Derin RNN’ ler - Deep RNN’ s : Bazı durumlarda tek katmanlı RNN’ ler işe yaramaz. Bu durumlarda Derin RNN’ ler kullanılır. Aşağıda bir örnek verilmiştir. <br>
 ![31.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/31.jpg) <br>
    - Not : a[2]<3> = g(W_a[2] * [a[2]<2>, <[1]<3> ] + b_a[2] ) <br><br><br>

  
  * <b> Doğal Dil İşleme ve Kelime Gömmeleri (  NAtural Language Processing and Word Embeddings ) </b> <br>
  
  * Kelime Gösterimi : Word Embedding, sözcükleri temsil etmenin bir yoludur. Algoritmanın, “kral” ve “kraliçe” gibi kelimeler arasındaki analojileri otomatik olarak anlamasını sağlar. Derslerde bu noktaya kadar gösterim için one-hot-encoding yöntemi kullanıldı. Buna bir örnek aşağıda verilmiştir :  <br>
     ![32.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/32.jpg) <br>
    - Bu temsilin genel dezavantajı, kelimeler arasında genelleştirmeye izin vermemesidir. Bu duruma bir örnek vermemiz gerekirse ;
      * “ I want a glass of orange __ “  cümlesi verildiğinde, model sonraki kelimeyimeyve suyu olarak tahmin etmelidir. 
      * “ I want a glass of apple __ “. Eğer model üzerinde bu cümle kullanılmamışsa model meyve suyunu tahmin edemez. Yani iki örnek için portakal ve elma kelimeleri arasında bir bağlam kurulamaz. 
    - Her hangi one-hot-encode vektörü arasında iç çarpım sıfırdır ve aralarındaki mesafeler de aynıdır.  Bu noktada one-hot-encode yerine , her kelime için özellikler ile bir temsil öğrenilebilse nasıl olur ?
  ![33.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/33.jpg) <br>
    - Bu örnekte her kelime, 300 özelliğe sahip olur. Yani her kelimenin 300 boyutlu bir vektörden oluştuğu söylenebilir. Anlatılan iki cümle örneğinie dönülecek olunursa; yukarıdaki 300 boyutlu vektör sayesinde portakal ve elma birçok özelliği paylaşmaktadır. Bu özellik paylaşımı ile iki kelime arasında bir genelleme yapılabilmektedir.  İşte bu yaklaşıma “Word Embedding”  denir. <br>
    - Word Embedding ‘ in bir görselleştirmesi için aşağıdaki örnek verilmiştir. 
   ![34.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/34.jpg) <br>
    - Burada da görüldüğü gibi, benzer kelimeler birbirine daha yakın konumlanmıştır. Yani one-hot-encoding’ de olduğu gibi her kelime arası mesafe eşit değildir. 
* Word Embedding kullanımı : 
    - Her bir kelime için oluşturulmuş word embedding lerin varlık tanıma problemleri üzerinde nasıl kullanıldığına bakacak olursak;
     ![35.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/35.jpg) <br>
  
    - Sally Johson özel addır. Bu cümle üzerinde yapılan eğitim sonucu model, başka bir cümle verildiği zaman özel isimleri bulabilmelidir. Öyle ki model daha önce görmediği bir kelimeyi cümlede almış olsa bile bunun özel bir isim olduğunu kavramalıdır. Word embedding kullanan algoritmalar, etiketlenmemiş metindeki kelimeleri inceleyebilir ve bunların temsilini öğrenebilir. 
* Transfer learning ve word embeddings : 
  - Büyük metin sözlüğünden word embedding’ ler öğrenilir. 
  - Daha küçük eğitim seti ile embedding yeni göreve aktarılır
  - İsteğe bağlı olarak word embedding’ lerde ince ayarlar yapılabilir. 
  - Word embedding’ ler one-hot-encoding yöntemine göre giriş boyutunu küçültmektedir. 
     ( one-hot-encoding’ te 1000 boyutlu girişler varken, word embedding 300 boyutlu vektörler kullanır. )
  - Word embedding’ ler  “face recognation” ile benzerdir. “Face recognation” da her yüz bir vektöre kodlanır ve sonraki vektörlerin bu vektör ile ne kadar benzer olduklarına bakılır. 
* Word embedding’ lerin özellikleri : Word embedding’ lerin bir diğer özelliği analoji karşılaştırmalarında yardımcı olabilmeleridir. Buna bir örnek verecek olursak ; <br>
   ![36.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/36.jpg) <br>
  
  - Bu tabloya göre şu soruya cevap verilmelidir : 
    * Kadın = erkek ise
    * Kraliçe = ? 
  - Kadın vektöründen erkek vektörünü çıkaralım. Elde edilecek vektör yaklaşık [ 2 0 0 0 ]’ dır. Benzer şekilde Kraliçe vektöründen kral vektörünü çıkarırsak da elde edilen vektör [ 2 0 0 0 ] olacaktır.  Yani elde edilen fark her ikisinde de cinsiyet farkıdır.
   ![37.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/37.jpg) <br>
  - Elde edilen bu vektör cinsiyet vektörüdür. Çizim, bir t-SNE algoritması tarafından çıkarılan 4B vektörün 2B görselleştirmesidir. Bu vektör sayesinde, kraliçe = kral diyebiliriz. Bu durum matematiksel olarak şu şekilde ifade edilebilir : <br>
  ![38.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/38.jpg) <br>
  - Burada benzer vektörü elde eden en iyi çözüm e_queen’ dir. 
* Kosinüs benzerliği : En çok kullanılan benzerlik yöntemidir. Denklemi :<br>
    ![39.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/39.jpg) <br>
  - Buradaki çarpımlar vekrtörlerin iç çarpımlarını ifade etmektedir. Vektörler çok benzer ise elde edilen değer büyük olur. Bu sebeple iklid mesafesi, bir benzerlik ölçütü olarak da kullanılabilir. Burada : 
    * u = e_w , v = e_king - e_man + e_woman olarak kullanılmalıdır.
* Embedding matris : Embedding kelimenin öğrenilebilmesi için bir algoritma kullanıldığında elde edilen matris, gömme matrisidir (embedding matrix ). 10.000 kelimelik bir kelime dağarcığı ve 300 özellik için elde edilen embedding matris boyutu (300, 10.000) ‘ dir. E ile gösterilir.<br>
 ![40.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/40.jpg) <br>
  - E ilk başta random olarak başlatılır, daha sonra parametreler için öğrenme gerçekleşir.
* Word Embedding’ leri öğrenme : Word2vec ve GloVe : Word embedding’ leri öğrenen bazı algoritmalar mevcuttur. 
  - Sinirsel Dil Modeli :  (https://www.jmlr.org/papers/volume3/bengio03a/bengio03a.pdf ).
    Aşağıdaki örnek üzerinden gidelim : <br>
   ![41.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/41.jpg) <br>
    Burada, sonraki kelimenin tahmin edilebilmesi için bir dil modeli oluşturulmalıdır. <br>
    ![42.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/42.jpg) <br>
    - e_j değeri , np.dot(E, o_j) ile elde edilir. 
    - NN katmanında W1 ve b1 parametreleri, softmax katmanında ise W2 ve b2 parametreleri bulunmaktadır. 
    - Tahmin edilen kelimeden önce 6 kelime olduğu için pencere ( window ) boyutu 6’ dır. Dolayısıyla girdi boyutu ( 300 * 6 , 1 )’ dir.  Burada, bağlam verildikten sonra tahmin olasılığını maksimuma çıkarmak için E matrisi ve katman parametreleri optimize edilir.
    - Yukarıdaki örnekte ele alınan 6 değeri dışında farklı değerler de kullanılabilir. Örneğin son 4 kelime, sol ve sağdan 4 kelime, son 1 kelime, en yakın ( word embedding için mesafeden söz ediyoruz. ) 1 kelime dikkate alınabilmektedir. <br><br>
* Word2Vec : ( referans link : https://arxiv.org/abs/1301.3781 ). Word2Vec’ ten önce skip-gram’ lardan bahsedelim. Örneğin “ I want a glass of orange juice to go along with my cereal.”  cümlesi için bağlam ve hedef seçilmelidir. Hedef değişkeni, belirli boyuta sahip bir pencereye göre seçilir. <br>
  ![43.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/43.jpg) <br>
  - Kelime dağarcığı 10.000, c bağlam kelimesi “portakal” ve hedef kelime t “meyve suyu” olsun. c’ den t’ ye haritalamanın öğrenilebilmesi için ; 
    * e_c = np.dot(E, o_c ) ile elde edilir.
    * Daha sonra ŷ için softmax katmanı ve 
    * Loss için cross-entropy kullanılır. <br>
   ![44.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/44.jpg) <br>
    * output_size = n = 10.000 olarak alınır.
    * Son katmana ait softmax aşağıda verilmiştir. <br>
   ![45.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/45.jpg) <br>
    * Burada kelime dağarcığında bulunan 10.000 kelime için bir toplama yapıyoruz. İşte tam bu noktada işlem maliyeti problemi ortaya çıkıyor. Çünkü eğer kelime dağarcığı 1M gibi çok yüksek rakamlardaysa işlem çok fazla zaman kaybettiriyor. Bu problemin çözülebilmesi için “Hiyerarşik Softmax Sınıflandırıcı “ kullanılmakta. <br>
   ![46.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/46.jpg) <br>
    * Bu yapıda, dengeli bir ağaç kullanılmaz ve en sık kullanılan kelimeler ağacın en üst noktasında yer alır. 
  - c bağlamı nasıl gösterilir ? : c’ yi göstermenin bir yolu, rastgele seçmektir. Ancak “the, a, to “ gibi kelimeler, rastgele seçim sırasında baskın gelebildiği için uygulamada bu yöntem kullanılmaz. Bunun yerine yaygın ve yaygın olmayan kelimelerin dengeli kullanımı için algoritmalar geliştirilmiştir. 
  - Word2Vec makalesi, word embedding’ lerin öğrenimi için 3 fikir içerir. Biri tlamalı gram modeli, diğeri ise CBoW ( sürekli kelime çantası ) modelidir. 
* Negatif Örnekleme : Negatif örnekleme, skip-gram modeline benzer olarak daha verimli bir örnekleme sağlar. “ I want a glass of orange juice to go along with my cereal.”  cümlesini tekrar ele alırsak negatif örnekleme şu şekildedir ; <br>
  ![47.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/47.jpg) <br>
  - Negatif bir örnek oluşturmak için, sözlükten rastgele bir örnek seçilir. Örnekler oluşturulurken ; 
    * Olumlu bir bağlam seçilir,
    * Sözlükten k tane olumsuz bağlam seçilir. Küçük veri setlerinde k’ nın 5-20 arasında olması önerilir. Daha büyük veri setleri için k değeri -2 ile 5 arasında olabilir. Burada oran; k olumsuz örneğe 1 olumlu örnek şeklinde olmalıdır. 
  - Bu işlemlerden sonra, denetimli öğrenme problemini öğrenecek modele gelirsek ; 
    * bağlam kelimesi c ve hedef kelimeler ise t ve y olsun. <br>  
  ![48.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/48.jpg) <br>
    * Uygulanan lojistik regresyon modeli ise şu şekildedir : <br>
  ![49.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/49.jpg) <br>
  - Negatif örnekler nasıl seçilir ? : Kelime dağarcığındaki kelimelerin frekanslarına göre bir örnekleme yapılabilmektedir. Ancak burada “of, the” gibi bazı kelimelerin frekansı yüksek olmaktadır. Bu nedenle uygun görülen en iyi örneklem : <br>
  ![50.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/50.jpg) <br>

  
  
  
  
  
  
  ![51.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/51.jpg) <br>
  
  ![52.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/52.jpg) <br>
  
  ![53.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/53.jpg) <br>

  
  
  
  
  
  
  
