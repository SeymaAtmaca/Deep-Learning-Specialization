
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

* Waa , RNN’ in önceki katmanlardan korumaya çalıştığı bellketir.  İLgili RNN mimarisinde y<t> çıkışı, bir önceki giriş ve aktivasyonlara bağlıdır. Yani y<4> çıkışı için hesapları sadece x<1>, x<2> ve x<3> etkiler. x<4> ün etkisi yoktur. <br><br>

![2.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/2.jpg) <br><br>

  
  
* Ancak bu RNN lerde ortayaçıkan sorun, sonraki bilgileri kullanamıyor olmasıdır. Örneğin “Teddy, bir başkandı”  cümlesinde Teddy isminin bir şahıs olduğu sonucuna başkan kelimesi ile varabiliyoruz ancak bu bilgi, ileriki seviyelerden alınamıyor. Bunun çözümü için “Çift Yönlü RNN”  kullanılmaktadır. 
* Mevcut, çift yönlü olmayan RNN ler için ileri besleme denklemleri : <br><br>
  
![3.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/3.jpg) <br><br>
  
* a’ nin aktivasyon fonksiyonu genelde tanh veya ReLU’ dur. Y için ise sigmoid veya softmax kullanılmaktadır. Özel isim- varlık modelinde iki sınıf yer aldığı için sigmoid örneği yapılmıştır. Bu son denklemleri biraz basitleştirerek ele alacak olursak basitleştirilmiş RNN gösterimi ; <br><br>

  ![4.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/4.jpg) <br><br>
  
  - Wa, Waa ve Wax in sıkıştırılmış gösterimidir.
  - Wa shape : ( gizli nöron sayısı, gizli nöron sayısı ) 
  - [a<t-1>, x<t> ] shape : ( gizli nöron sayısı + n_x , 1)
  
* Bonus : Ayrıntılı RNN tek cell görünümü : <br><br>
  ![5.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/5.jpg) <br><br>
  
* RNN : <br><br>
    ![6.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/6.jpg) <br><br>
  
  
* Zaman içinde geri yayılım : Geri yayılım, ileri yayılım yapıldıktan sonra sistemler tarafından otomatik olarak gerçekleştirilir. Ancak RNN’ lerde ayrıntılı incelenmesi bir artıdır. Geri yayılım grafiği ; <br><br>
   ![7.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/7.jpg) <br><br>
  
* Burada Wy, by, Wa, ba her dizi öğesi için ortak kullanılmaktadır. RNN hücresinde genel geri yayılıma bakılacak olunursa ; <br><br>
  ![8.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/8.jpg) <br><br>
 
* Burada cross-entropy fonksiyonu kullanılacak olursa ; <br><br>
  ![9.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/9.jpg) <br><br>

* Loss ile yayılım akışı : <br><br>
  ![10.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/10.jpg) <br><br>
  
  - kırmızı oklar geri yayılımı belirtir. Loss, zaman içindeki geri yayılımdır. <br>
  
* Farklı RNN Türleri :  <br><br>
  ![11.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/11.jpg) <br><br>
  - bir müzik üretimi modeli, birden çoğa mimari örneğidir. Üretilen sonuç, ağda geri beslenir ; <br><br>
  ![12.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/12.jpg) <br><br>
  - Makine çevirisi modelleri, many-to-many mimarisine örnektir. Kodlayıcı, giriş dizisini bir matrise çevirir ve çıkışları oluşturmak için bunu kod çözücüye besler. Çeviri için örnek bir many-to-many mimarisi ;  <br><br>
  ![13.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/13.jpg) <br><br>
  - RNN türlerinin genel özeti ; <br><br>
  ![14.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/14.jpg) <br><br>
* Dil Modeli ve Dizi Oluşturma : Bir dil modeli uygulamasında, ses açısından benzer iki cümle arasında bir olasılık değeri üzerinden seçim yapılabilmesi için dil modelelri kullanılıyor. Burada benzer cümleler için verilen örnek : 
  - The apple and pair salad
  - The apple and pear salad
	 Bu örnekte kararın verildiği nokta pair-pear bölümüdür. Dil modeli hangi kelimenin doğru seçenek olduğunu belirtmek için iki kelime adına birer olasılık değeri döndürerek seçim yapılmasını sağlar.Bir dil modelinin işi, verilen herhangi bir sözcük dizisinin olasılığını vermektir.
* RNN’ lerde dil modelleri nasıl oluşturulur ? : 
  - İlk olarak eğitim veri seti için büyük bir hedef dil metni sözlüğü oluşturulmalıdır.
  - Daha sonra bu sözlük üzerinde her kelime teker teker okunarak birer simgeye dönüştürülür. 
  - Cümle sonlarını ifade etmek için <EOS> ve bilinmeyen yeni kelimeler için <UNK> simgesi eklenir. 
* “Kediler günde 15 saat uyurlar. <EOS>”  - ( “Cats average 15 hours of sleep a day. <EOS> “)  cümle örneği üzerinden konu ele alınmıştır.  Eğitim sürecinde ; <br><br>
  ![15.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/15.jpg) <br><br>
  
* Loss için cross-entropy kullanılır ;  <br><br>
  ![16.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/16.jpg) <br><br>
  
  Burada i, kelimeleri, t ise zamanı ifade etmektedir. Bu modelin kullanımında ; 
  1) Bir sonraki kelimenin olasılığını tahmin etmek için cümle RNN’ e beslenir. Daha sonra son y^<t> vektörü maksimum olasılığa göre sıralanır. 
  2) Bir cümleye ait genel olasılık hesabında ise aşağıdaki işlem yapılır ; 
    - P(y^<1>, y^<2>, y^<3> ) = P(y^<2> | y^<1> ) * P(y^<1>, y^<2>)
    - Kısaca cümle RNN’ e beslenmiş ve olasılıkları çarpılmış olur.   
* Yeni dizilerin örneklenmesi : 
  - Bir dil modelinin, eğitildikten sonra yeni diziler üzerinde kullanımı aşağıda verilmiştir.
    1) Aşağıdaki model göz önüne alınırsa ; <br> <br>
    ![17.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/17.jpg) <br><br>
    2) İlk olarak a^<0> ve x^<1> zeros vektörleri modele gönderilir.
    3) Daha sonra ilk çıktı olan ŷ <1> ile elde edilen dağılımdan rastgele bir tahmin seçilir. Örneğin bu tahmin “The “ olabilir. Numpy üzerinde bu rastgele seçim işlemi “numpy.random.choice() “ ile yapılmaktadır. Bu satır, yeni bir dizi modele uygulandığında, cümlenin ilk kelimesini rastgele seçilmesini sağlar. 
    4) ŷ <2> ‘ nin hesabı için son tahmin edilen kelime olan ŷ <1> ve a <2> değerleri kullanılır. 
    5) <EOS> simgesi gelene kadar bu tahmin işlemleri devam eder. <br><br>
![18.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/18.jpg) <br><br>
 
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
    - Exploding Gradients : Patlayan gradyan çözümünde kullanılan bir yöntem, gradyanın bir eşik değerden fazla olduğu durumlarda degrade kırpma kullanımıdır. Bu noktada, gradyan vektörünün bir kısmı yeniden ölçeklendirilmiş olur. Aşağıda gradyan kırpma için bir örnek verilmiştir. <br><br>
  ![19.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/19.jpg) <br><br>
  
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
    - Temel RNN birimi :<br> <br>
    ![20.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/20.jpg) <br><br>
    - GRU’ larda her katman için atanan ve unutup-unutmama durumunu ifade eden c bellek hücresi değişkeni vardır. c <t> = a <t> dir. GRU’ lara ait denklemler :<br> <br>
    ![21.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/21.jpg) <br><br>
  Burada c^<t-1> eski değer ve  c̃ <t> aday değerdir. <br>
    - Update gate ( güncelleme kapısı ) , Gama olarak adlandırılır ve 0 - 1 arasında değer alır. Güncelleme kapısı sayesinde mevcut hafıza hücres, önceki hücreye göre güncellenebilir.<br> <br>
   ![22.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/22.jpg) <br><br>
  
    - Dersin bu noktasında kaynak gösterilen link : http://colah.github.io/posts/2015-08-Understanding-LSTMs/ 
    - Daha önce verilen kedi örneğinden ( the cat, which already ate …, was full ) devam edilirse;
      * U’ nun 0-1 olduğunu ve tekil bir kelimenin ezberlenip ezberlenmemesi gerektiğini söyleyen bir bit olduğunu düşünelim.Burada kelimeleri bölüp, C ve U değerlerini teker teker alacak olursak ; <br><br>
  ![23.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/23.jpg) <br><br>
      * GRu’ larda, U 0.00001 gibi çok küçük değerlerde olduğu için vanishing gradient problemi yaşanmaz. 
      * Shapes :
        1) a^<t> : ( gizli_nöron_sayısı, 1)
        2) c^<t> : (gizli_nöron_sayısı, 1) 
        3) c~<t> : (gizli_nöron_sayısı, 1) 
        4) u^<t> : (gizli_nöron_sayısı, 1) 
        - NOT : Denklemlerde bulunan çarpma, eleman bazlı çarpmadır. 
        - Bu noktaya kadar açıklanan GRU, Basitleştirilmiş - Simplified GRU’ dur. Buradan sonra Full GRU açıklanacaktır. Full GRU, bir sonraki c tahmini için kullanılır. Bir önceki c değerinin ( c^<t-1> ) , bir sonraki c değerini ( c^<t> ) nasıl etkilediğini, ne derece bağımlı olduğunu açıklamak için kullanılır.  <br><br>
  ![24.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/24.jpg) <br><br>
        - Yukarıdaki formülde r_u ( gama_r ), ilgi düzeyini göstermektedir. 
* LSTM ( Uzun Kısa süreli bellek ) :  LSTM, uzun vadeli bağımlılıkları tutabilmek için kullanılan bir RNN türüdür. ( NOT : LSTM için açıklayıcı bir link : https://mfakca.medium.com/lstm-nedir-nas%C4%B1l-%C3%A7al%C4%B1%C5%9F%C4%B1r-326866fd8869 ) GRU’ larda c^<t> = <^<t> iken, LSTM’ lerde c^<t>, a^<t>’ ye eşit değildir. LSTM’ e ait denklemler aşağıda verilmiştir. <br><br>
   ![25.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/25.jpg) <br> <br>
        - LSTM’ e ait genel bir yapı ; <br><br>
  ![26.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/26.jpg) <br><br>
        - Yukarıdaki bu temel yapı birimleri ise birbirine şu şekilde bağlanmaktadır ; <br><br>
    ![27.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/27.jpg) <br><br>
        - Genel olarak bakıldığında GRU’ lar daha basittir ve daha büyük ağların kurulmasında kullanılabilir. Ancak LSTM’ ler daha güçlüdür. LSTM’ e ait hücre geri yayılımı aşağıda verilmiştir. <br><br>
  ![28.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/28.jpg) <br><br>
 
* Çift Yönlü RNN ( Bidirectional RNN ) : Dizi modellerini daha güçlü hale getirebilmek için LSTM, GRu dışında kullanılabilecek bir diğer yapılar ise Bidirectional RNN’ ve Deep RNN’ lerdir. <br><br>
  ![29.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/29.jpg) <br>  <br>
  - Bu örnekte Teddy ismi bear ile çözümlenebilir. Bu noktada algılama probleminin çözülebilmesi için Bidirectional RNN’ ler kullanılır. BiDirectional RNN lerin genel yapısı aşağıda verilmiştir.<br><br>
     ![30.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/30.jpg) <br><br>
    - Görüldüğü gibi yapı döngüsel değildir. İleri yayılımın bir kısmı soldan sağa, bir kısmı sağdan sola ilerler. Bu sayede her iki taraftan da öğrenme gerçekleşmiş olur. Tahmin aşamasında hem sol hem de sağdan gelen iki aktivasyon çıktısı da kullanılır ve  ŷ <t> hesaplanır. 
    - Buradaki bloklar, temel RNN’ ler , LSTM’ ler veya GRU’ lar da dahil olmak üzere herhangi bir RNN olabilmektedir.
    - Bidirectional RNN’ lerin dezavantajı ise, işlemek için tüm diziye ihtiyaç duyulmasıdır. Bu da gerçek zamanlı kullanımlarda gecikmelere sebep olabilmektedir.
  
* Derin RNN’ ler - Deep RNN’ s : Bazı durumlarda tek katmanlı RNN’ ler işe yaramaz. Bu durumlarda Derin RNN’ ler kullanılır. Aşağıda bir örnek verilmiştir. <br><br>
 ![31.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/31.jpg) <br><br>
    - Not : a[2]<3> = g(W_a[2] * [a[2]<2>, <[1]<3> ] + b_a[2] ) <br><br><br>

  
  * <b> Doğal Dil İşleme ve Kelime Gömmeleri (  NAtural Language Processing and Word Embeddings ) </b> <br>
  
  * Kelime Gösterimi : Word Embedding, sözcükleri temsil etmenin bir yoludur. Algoritmanın, “kral” ve “kraliçe” gibi kelimeler arasındaki analojileri otomatik olarak anlamasını sağlar. Derslerde bu noktaya kadar gösterim için one-hot-encoding yöntemi kullanıldı. Buna bir örnek aşağıda verilmiştir :  <br><br>
     ![32.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/32.jpg) <br><br>
    - Bu temsilin genel dezavantajı, kelimeler arasında genelleştirmeye izin vermemesidir. Bu duruma bir örnek vermemiz gerekirse ;
      * “ I want a glass of orange __ “  cümlesi verildiğinde, model sonraki kelimeyimeyve suyu olarak tahmin etmelidir. 
      * “ I want a glass of apple __ “. Eğer model üzerinde bu cümle kullanılmamışsa model meyve suyunu tahmin edemez. Yani iki örnek için portakal ve elma kelimeleri arasında bir bağlam kurulamaz. 
    - Her hangi one-hot-encode vektörü arasında iç çarpım sıfırdır ve aralarındaki mesafeler de aynıdır.  Bu noktada one-hot-encode yerine , her kelime için özellikler ile bir temsil öğrenilebilse nasıl olur ?<br><br>
  ![33.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/33.jpg) <br><br>
    - Bu örnekte her kelime, 300 özelliğe sahip olur. Yani her kelimenin 300 boyutlu bir vektörden oluştuğu söylenebilir. Anlatılan iki cümle örneğinie dönülecek olunursa; yukarıdaki 300 boyutlu vektör sayesinde portakal ve elma birçok özelliği paylaşmaktadır. Bu özellik paylaşımı ile iki kelime arasında bir genelleme yapılabilmektedir.  İşte bu yaklaşıma “Word Embedding”  denir. <br>
    - Word Embedding ‘ in bir görselleştirmesi için aşağıdaki örnek verilmiştir. <br><br>
   ![34.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/34.jpg) <br><br>
    - Burada da görüldüğü gibi, benzer kelimeler birbirine daha yakın konumlanmıştır. Yani one-hot-encoding’ de olduğu gibi her kelime arası mesafe eşit değildir. 
* Word Embedding kullanımı : 
    - Her bir kelime için oluşturulmuş word embedding lerin varlık tanıma problemleri üzerinde nasıl kullanıldığına bakacak olursak;<br><br>
     ![35.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/35.jpg) <br><br>
  
    - Sally Johson özel addır. Bu cümle üzerinde yapılan eğitim sonucu model, başka bir cümle verildiği zaman özel isimleri bulabilmelidir. Öyle ki model daha önce görmediği bir kelimeyi cümlede almış olsa bile bunun özel bir isim olduğunu kavramalıdır. Word embedding kullanan algoritmalar, etiketlenmemiş metindeki kelimeleri inceleyebilir ve bunların temsilini öğrenebilir. 
* Transfer learning ve word embeddings : 
  - Büyük metin sözlüğünden word embedding’ ler öğrenilir. 
  - Daha küçük eğitim seti ile embedding yeni göreve aktarılır
  - İsteğe bağlı olarak word embedding’ lerde ince ayarlar yapılabilir. 
  - Word embedding’ ler one-hot-encoding yöntemine göre giriş boyutunu küçültmektedir. 
     ( one-hot-encoding’ te 1000 boyutlu girişler varken, word embedding 300 boyutlu vektörler kullanır. )
  - Word embedding’ ler  “face recognation” ile benzerdir. “Face recognation” da her yüz bir vektöre kodlanır ve sonraki vektörlerin bu vektör ile ne kadar benzer olduklarına bakılır. 
* Word embedding’ lerin özellikleri : Word embedding’ lerin bir diğer özelliği analoji karşılaştırmalarında yardımcı olabilmeleridir. Buna bir örnek verecek olursak ; <br><br>
   ![36.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/36.jpg) <br><br>
  
  - Bu tabloya göre şu soruya cevap verilmelidir : 
    * Kadın = erkek ise
    * Kraliçe = ? 
  - Kadın vektöründen erkek vektörünü çıkaralım. Elde edilecek vektör yaklaşık [ 2 0 0 0 ]’ dır. Benzer şekilde Kraliçe vektöründen kral vektörünü çıkarırsak da elde edilen vektör [ 2 0 0 0 ] olacaktır.  Yani elde edilen fark her ikisinde de cinsiyet farkıdır.<br><br>
   ![37.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/37.jpg) <br><br>
  - Elde edilen bu vektör cinsiyet vektörüdür. Çizim, bir t-SNE algoritması tarafından çıkarılan 4B vektörün 2B görselleştirmesidir. Bu vektör sayesinde, kraliçe = kral diyebiliriz. Bu durum matematiksel olarak şu şekilde ifade edilebilir : <br><br>
  ![38.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/38.jpg) <br><br>
  - Burada benzer vektörü elde eden en iyi çözüm e_queen’ dir. 
* Kosinüs benzerliği : En çok kullanılan benzerlik yöntemidir. Denklemi :<br><br>
    ![39.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/39.jpg) <br><br>
  - Buradaki çarpımlar vekrtörlerin iç çarpımlarını ifade etmektedir. Vektörler çok benzer ise elde edilen değer büyük olur. Bu sebeple iklid mesafesi, bir benzerlik ölçütü olarak da kullanılabilir. Burada : 
    * u = e_w , v = e_king - e_man + e_woman olarak kullanılmalıdır.
* Embedding matris : Embedding kelimenin öğrenilebilmesi için bir algoritma kullanıldığında elde edilen matris, gömme matrisidir (embedding matrix ). 10.000 kelimelik bir kelime dağarcığı ve 300 özellik için elde edilen embedding matris boyutu (300, 10.000) ‘ dir. E ile gösterilir.<br><br>
 ![40.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/40.jpg) <br><br>
  - E ilk başta random olarak başlatılır, daha sonra parametreler için öğrenme gerçekleşir.
* Word Embedding’ leri öğrenme : Word2vec ve GloVe : Word embedding’ leri öğrenen bazı algoritmalar mevcuttur. 
  - Sinirsel Dil Modeli :  (https://www.jmlr.org/papers/volume3/bengio03a/bengio03a.pdf ).
    Aşağıdaki örnek üzerinden gidelim : <br><br>
   ![41.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/41.jpg) <br><br>
    Burada, sonraki kelimenin tahmin edilebilmesi için bir dil modeli oluşturulmalıdır. <br><br>
    ![42.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/42.jpg) <br><br>
    - e_j değeri , np.dot(E, o_j) ile elde edilir. 
    - NN katmanında W1 ve b1 parametreleri, softmax katmanında ise W2 ve b2 parametreleri bulunmaktadır. 
    - Tahmin edilen kelimeden önce 6 kelime olduğu için pencere ( window ) boyutu 6’ dır. Dolayısıyla girdi boyutu ( 300 * 6 , 1 )’ dir.  Burada, bağlam verildikten sonra tahmin olasılığını maksimuma çıkarmak için E matrisi ve katman parametreleri optimize edilir.
    - Yukarıdaki örnekte ele alınan 6 değeri dışında farklı değerler de kullanılabilir. Örneğin son 4 kelime, sol ve sağdan 4 kelime, son 1 kelime, en yakın ( word embedding için mesafeden söz ediyoruz. ) 1 kelime dikkate alınabilmektedir. <br><br>
* Word2Vec : ( referans link : https://arxiv.org/abs/1301.3781 ). Word2Vec’ ten önce skip-gram’ lardan bahsedelim. Örneğin “ I want a glass of orange juice to go along with my cereal.”  cümlesi için bağlam ve hedef seçilmelidir. Hedef değişkeni, belirli boyuta sahip bir pencereye göre seçilir. <br><br>
  ![43.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/43.jpg) <br><br>
  - Kelime dağarcığı 10.000, c bağlam kelimesi “portakal” ve hedef kelime t “meyve suyu” olsun. c’ den t’ ye haritalamanın öğrenilebilmesi için ; 
    * e_c = np.dot(E, o_c ) ile elde edilir.
    * Daha sonra ŷ için softmax katmanı ve 
    * Loss için cross-entropy kullanılır. <br><br>
   ![44.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/44.jpg) <br><br>
    * output_size = n = 10.000 olarak alınır.
    * Son katmana ait softmax aşağıda verilmiştir. <br><br>
   ![45.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/45.jpg) <br><br>
    * Burada kelime dağarcığında bulunan 10.000 kelime için bir toplama yapıyoruz. İşte tam bu noktada işlem maliyeti problemi ortaya çıkıyor. Çünkü eğer kelime dağarcığı 1M gibi çok yüksek rakamlardaysa işlem çok fazla zaman kaybettiriyor. Bu problemin çözülebilmesi için “Hiyerarşik Softmax Sınıflandırıcı “ kullanılmakta. <br><br>
   ![46.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/46.jpg) <br><br>
    * Bu yapıda, dengeli bir ağaç kullanılmaz ve en sık kullanılan kelimeler ağacın en üst noktasında yer alır. 
  - c bağlamı nasıl gösterilir ? : c’ yi göstermenin bir yolu, rastgele seçmektir. Ancak “the, a, to “ gibi kelimeler, rastgele seçim sırasında baskın gelebildiği için uygulamada bu yöntem kullanılmaz. Bunun yerine yaygın ve yaygın olmayan kelimelerin dengeli kullanımı için algoritmalar geliştirilmiştir. 
  - Word2Vec makalesi, word embedding’ lerin öğrenimi için 3 fikir içerir. Biri tlamalı gram modeli, diğeri ise CBoW ( sürekli kelime çantası ) modelidir. 
* Negatif Örnekleme : Negatif örnekleme, skip-gram modeline benzer olarak daha verimli bir örnekleme sağlar. “ I want a glass of orange juice to go along with my cereal.”  cümlesini tekrar ele alırsak negatif örnekleme şu şekildedir ; <br><br>
  ![47.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/47.jpg) <br><br>
  - Negatif bir örnek oluşturmak için, sözlükten rastgele bir örnek seçilir. Örnekler oluşturulurken ; 
    * Olumlu bir bağlam seçilir,
    * Sözlükten k tane olumsuz bağlam seçilir. Küçük veri setlerinde k’ nın 5-20 arasında olması önerilir. Daha büyük veri setleri için k değeri -2 ile 5 arasında olabilir. Burada oran; k olumsuz örneğe 1 olumlu örnek şeklinde olmalıdır. 
  - Bu işlemlerden sonra, denetimli öğrenme problemini öğrenecek modele gelirsek ; 
    * bağlam kelimesi c ve hedef kelimeler ise t ve y olsun. <br>  <br>
  ![48.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/48.jpg) <br><br>
    * Uygulanan lojistik regresyon modeli ise şu şekildedir : <br><br>
  ![49.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/49.jpg) <br><br>
  - Negatif örnekler nasıl seçilir ? : Kelime dağarcığındaki kelimelerin frekanslarına göre bir örnekleme yapılabilmektedir. Ancak burada “of, the” gibi bazı kelimelerin frekansı yüksek olmaktadır. Bu nedenle uygun görülen en iyi örneklem : <br><br>
  ![50.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/50.jpg) <br><br>

  - Denklemde verilen f(a), a kelimesinin gözlenme sıklığını ifade etmektedir. 
* Word embedding’ lerle ilgili çıkan sonuçlar : 
	- İlk kullanımlarda, daha önce kullanılmış ve iyi sonuç vermiş, eğitilmiş bir model kullanılmalıdır. 
	- Yeterli veri bulunması durumunda, mevcut algoritmalar kullanılabilir. 
	- Word embedding’ leri eğitmek, hesaplama açısından çok pahalı olduğundan, çoğu makine öğrenimini kullanan kişiler, embedding’ ler için pre-trained set kullanır.
* Word Embedding Kullanan Uygulamalar : 
	a) Sentiment Classification : Bir metnin olumlu-olumsuz olma durumunu değerlendirir. Örneğin bir film için yazılan yorumun olumlu-olumsuzluk durumu değerlendirilir ve yıldız oluşturulur. NLP’ lerde çok faydalıdır ve pek çok noktada kullanılır. Sentiment Classification için bir örnek aşağıda verilmiştir : <br><br> 
  ![51.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/51.jpg) <br><br>
		- Bu noktada karşılaşılacak en önemli problem, yeterli etiketli eğitim veri seti olmamasıdır. Ancak word embedding’ ler bu problemi çözer. Ortak veri seti boyutları 10.000 ile 100.000 arasında değişmektedir.  Basit bir sentiment classification örneği aşağıda verilmiştir. <br><br>
  ![52.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/52.jpg) <br><br>
  		- Bu örnekte özellik sayısı 300’ dür. Embedding matrisi 100 milyar kelime üzerinde eğitilmiş olabilir. Modelde, verilen tüm kelimelerin toplamını ve ortalamasını kullanabilir , ardından bunu bir softmax sınıflandırıcısına iletebilir. Bu, sınflandırıcının uzun ve kısa cümleler için çalışmasını sağlar.

		- Yukarıdaki modelde en belirgin sorun, sözcük sırasının göz ardı edilmesidir. Örneğin “İyi hizmet ve iyi ambiyans’ tan yoksun” yorumunda “iyi” sözcüğü birden fazla geçmektedir ancak yorum genel anlamda olumsuzdur. Bu olumsuzluğu veren ifade, cümlenin sonudna bulunan “yoksun”  sözcüğüdür. 
		- Bu sorunun çözülebilmesi için RNN kullanılabilir. Aşağıda bir örnek verilmiştir. <br><br>
  ![53.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/53.jpg) <br><br>
		- Bu algoritma eğitildiğinde iyi bir sentiment classification sonucu alınabilir. Ayrıca, daha iyi genelleme yapabilmektedir. Örneğin , “ İyi hizmet ve iyi ambiyanstan yoksun” cümlesindeki “yok” ifadesi etiketli eğitim veri setinde olmasa bile, kelime dağarcığı göz önüne alınarak iyi bir word embedding yapılabilir. 

* Word embedding’ leri azaltma : 
	- Word embedding’ lerin etnik köken gibi önyargılardan arındırılmış olması gerekir. Bazı word embedding’ lerden alınmış önyargı örnekleri aşağıda verilmiştir.
		* erkek : yazılım mühendisi, kadın : ev hanımı
		* baba : doktor, anne: hemşire <br><br>
 	 ![54.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/54.jpg) <br><br>
	- Bu önyargıların giderilmesi için : 
		1) Yön tanımlaması : 
			* Aradaki fark hesaplanır : ( e_male, e_female, e_he, e_she, ..)
			* Bazı k farkları seçilir ve ortalaması alınır. Bu seçim ile aşağıdaki sonuca varılır. <br><br>
  ![55.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/55.jpg) <br><br>
			* Bu sayede, bias vektörü olan 1D ve non-bias vektörü olan 299D bulunmuş olur. 
		2) Nötrleştirme : Tanımlayıcı olmayan (not definitional ) her kelime için önyargıdan kurtulma işlemi yapılır. Aşağıda bebek bakıcısı ve doktorun tarafsız olmasını sağlamak için önyargısız eksene yansıtma yapılmıştır. <br><br>
  ![56.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/56.jpg) <br><br>
		3) Çiftleri eşitleme : Her çift için sadece bir cinsiyet farkı olması gerekmektedir. ( dede- anneanne, kız-erkek, kadın- adam ) . Çift eşitleme bu şekilde yapılmıştır çünkü dede ile bakıcı arasındaki mesafe, bakıcı ile anneanne arasındaki mesafeden daha büyüktür. <br><br>
  ![57.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/57.jpg) <br><br>
			- Bu eşlemenin yapılabilmesi için dede- anneanne noktaları, non-bias noktasının ortasında olacakları yeni noktalara ( mor noktalar ) taşınmıştır. <br><br>
  ![58.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/58.jpg) <br><br>
			- Diğer noktalar da bu örnekteki gibi yeni noktalara taşınır.
			- Daha fazla ayrıntı için orijinal makale → https://arxiv.org/abs/1607.06520 
* Dizi Modelleri ve Dikkat Mekanizması : Bir dizi modelinin başarımı, dikkat mekanizmaları kullanılarak artırılabilir. Bu algoritma, model bir girdi aldığında hangi noktalara odaklanması gerektiğini anlamasında yardımcı olur. 
* Farklı sequence - to - sequence modelleri | temel modeller : 
	- X’  in bir Fransizce dizisi ( Fransızca cümle ) ve Y’ nin bir İngilizce dizisi olduğu bir makine çevirisi göz önüne alınsın. <br><br>
  ![59.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/59.jpg) <br><br>
	- Mimari, kodlayıcı ve kod çözücü ( encoder - decoder ) içermektedir. 
	- Kodlayıcı RNN’ dir ( LSTM ve GRU olabilir . ) ve giriş sırası alınır. Ardından tüm girişi temsil etmesi için bir vektör çıkarılır. Bu noktadan sonra kod çözücü ağı ( RNN ), kodlayıcı tarafından oluşturulan diziyi alır ve yeni bir dizi oluşturur. <br><br>

  ![60.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/60.jpg) <br><br>
	- ( Dersin temelinde kaynak alınan makaleler :  https://arxiv.org/abs/1409.3215, https://arxiv.org/abs/1406.1078 ) 

	- Bu mimariye örnek kullanılan bir problem, görüntüden altyazı üretimidir. Aşağıda buna dair bir örnek verilmiştir. X girdisi görüntü ve Y çıktısı ise cümledir. <br> <br>

  ![61.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/61.jpg) <br><br>
	- Burada kodlayıcı olarak CNN (Alexnet vb ) ve kod çözücü olarak ise RNN kullanılır. 
	- Bu örnek için kullanılan makaleler :  https://arxiv.org/abs/1412.6632 , https://arxiv.org/abs/1411.4555 , https://cs.stanford.edu/people/karpathy/cvpr2015.pdf ) 

* En olası cümlenin seçimi : Daha önce ele alınan dil modeli ile makine çevirisi modeli arasında benzerlik ve farklılıklar vardır.  Aşağıda kod çözücü kısmı benzerliği için bir görsel verilmiştir. <br><br>
  ![62.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/62.jpg) <br><br>
	- Dil modeli, tamamen sıfır olan bir ilk temsille başlatılırken, makine çevirisi modeli ilk etapta bir kodlanmış ağ kullanır. ( Koşullu dil modeli ) 
	- Ayrıca problem formülasyonları da farklıdır. 
		* Dil modeli : P(y^<1>, .. y^<Ty> )
		* Makine çevirisi : P(y^<1>, .. , y^<Ty> | x^<1>, .., x^<Ty> )
	- Makine çevirisi modelinde çıktı rastgele örneklenmek istenmez. Kötü çıktılar alınabilir. Duruma bir örnek aşağıda verilmiştir: 
		* X = “Jane Eylül’ de Afrika’ ya gidecek .“
		* Y şunlardan biri olabilir : 
		* “Jane, Eylül ayında Afrika’ ya gidecek.”
		* “Jane, Eylül’ de Afrika’ ya gidiyor.”
	- Bu nedenle çıtkıda en iyi seçeneğin alınması gerekmektedir. En yaygın algoritma, bean algoritmasıdır. Neden greedy algoritması kullanılmıyor ? : 
		* Bu durum bir örnekle açıklanacak olunursa : 
		* En iyi çıktı : “Jane is visiting Africa in September.” olsun.
		* Greedy ile bir seçim yapıldığında ilk iki kelime “Jane is” olsun. Bundan sonra “going” kelimesi seçilebilir, çünkü is’ den sonra en çok kullanılan kelime “going” tir. Yani bu seçim sonrası çıktı cümlesi şu şekilde oluşur : “Jane is going to be visiting Africa in September”. Görüldüğü gibi istenen çıktı elde edilememiş oluyor. 

* Bean Search : Bean search, en iyi çıktıyı elde etmek için kullanılan sezgisel algoritmadır. Bir önceki örnekten devam edecek olursak, yine istenen çıktı Y = “ Jane is visiting Africa in September” dır. 
	- Algoritma, B genişliği olan bir parametredir. Burada B = 3 olması, algoritmanın bir seferde 3 olası çıktıyı dikkate alacağı anlamına gelir. 
	- İlk adım için 10.000 oalsılık arasından ilk kelimeler için en iyi 3 aday [“in”, “jane”, “september”]’ dır. <br><br>
	
  ![63.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/63.jpg) <br><br>
	- Ardından, ilk çıktıdaki her kelime için en iyi ikili B kombinasyonları seçilir. Burada en iyi değer, olasılık çarpımları en yüksek değeri veren ikilidir.  
	( P(y^<1>, y^<2> | x ) = P(y^<1> | x ) * P(y^<2> | x,y^<1> ) ) <br><br>
  ![64.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/64.jpg) <br><br>
	- Bu, toplamda 30.000 kelime seçme yapılması gerektiği anlamına gelmektedir. Ve olası çıktının değerlendirilmesi için 3 kopya üretilmelidir. ( her kopya için 10.000 olasılık ) 
	- Çıktıda [“september”, “jane is”, “jane visits”] olacaktır. Dikkat edildiği üzere beam search bu üçlüyü ele alırsa ilk kelime “september” dır. 
	- Buradan sonra işlem tekrarlanır ve sonraki kelimeler ulunur.  <br><br>

  ![65.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/65.jpg) <br><br>
	- Bu algoritmada, ağda yalnızca B örnekleri saklanır. Yani her adımda B * N seçenek ile çalışılır. Eğer B = 1 ise bu, greedy search yapıldığı anlamına gelir. 

* Bean search için iyileştirmeler : 
	a) İlk iyileştirme çalışması, uzunluk optimizasyonu ( length optimization ) ‘ dur. <br> <br>
  ![66.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/66.jpg) <br><br>
		- Optimize etmek için  P(y<1> | x) * P(y<2> | x, y<1>) * ... * P(y<t> | x, y<y(t-1)>) çarpımı yapılır.
		- Olasılıklar çoğu zaman küçük kesirlerden oluşur. Ancak bu küçük kesirlerin çarpımı, sayısal taşmalara sebep olabilmektedir. Bu nedenle doğrudan çarpma yerine aşağıdaki işlem yapılır. <br><br>
  ![67.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/67.jpg) <br><br>
		- Burada uzun dizilerin işlenebilmesi için bu formülün aşağıdaki şekilde düzenlenmesi gerekmektedir. <br><br>
  ![68.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/68.jpg) <br><br>
		- Formülde ifade edilen alpha değeri hiperparametredir. Eğer alpha = 0 ise dizi uzunluğu için normalleştirme yapılmaz, alpha = 1 ise tam bir dizi uzunluğu normalleştirmesi yapılır. Pratikte bu değer 0.7 olarak ayarlanır. 
	b) En iyi bean genişliği ( B ) nasıl seçilir ? : B ne kadar büyük seçilirse, o kadar büyük olasılıklar göz önünde bulundurulur, sonuç da bir o kadar iyileştirilir. 
* Bean Search için Hata Analizi : Modelde alınan hatalı çıktının sebebinin B hiperparametresinden mi yoksa RNN’ den mi kaynaklandığını tespit etmek için hata analizi yapılır. Bunun yapılabilmesi için ( y^* : doğru cevap , y^ : model çıktısı o.ü. )  P(y^* | X ) ve P (y^ | X ) hesaplanır. Bu hesaplar için iki durum vardır : 
	1) P(y * | X) >  P(ŷ | X) : Böyle bir durumda hata Bean search’ ten kaynaklanır.
	2) P(y * | X) ≤ P(ŷ | X) : Burada ise hata RNN’ den kaynaklanmıştır. 
* BLEU Skor : Makine çevirisinin zorluklarından biri, bir dilde çeviri yapılması gerektiğinde, diğer dilde birden çok çevirinin olmasıdır.( Problemin çözümü için kullanılan kaynak makale : https://aclanthology.org/P02-1040.pdf ). Bu noktada seçim yapılabilmesi için BLEU puanı kullanılmaktadır. Buradaki mantık : Makine tarafından oluşturulan çeviri, insanlar tarafından sağlanan referanslardan herhangi birine oldukça yakın olduğu sürece, yüksek bir BLEU puanı elde edilecektir. Bir örnek üzerinden gidelim : 
	- X = “ Le chat est sur le tapis.”
	- Y1 = “The cat is on the mat.” ( insan kaynağı 1 ) 
	- Y2 = “ There is a cat on the mat.” ( insan kaynağı 2 ) 
	- Bu örnek için makinenin “the the the the” çıktısını verdiğini düşünelim. Makine çıktısını değerlendirmenin bir yolu, çıktıdaki her kelimeye bakmak ve referanslarda olup olmadığını kontrol etmektir. Bu işleme kısaca kesinlik denmektedir. Verilen makine çıktısı için kesinlik : 7/7’ dir, çünkü “the” iki insan kaynağında da vardır. Görüldüğü gibi bu değerlendirme kullanışlı değildir. 
	- Daha etkili bir değerlendirme için, kelimenin maksimum sayısıyla, referans bir kesinlik değeri kullanılabilir. Bu durumu şu şekilde açıklayabiliriz : 
değiştirilmiş hassasiyet : 2/7’ dir. Çünkü “the” kelimesi için maksimum kullanılma sayısı Y1’ dedir ve bu değer 2’ ye eşittir. Bu şekilde, kullanılan her kelime için bir oran oluşturulur. (unigram, n-gram ) 
* Bigram’ larda BLEU puanı : N-gramlar tipik olarak bir metin veya konuşma dağarcığından toplanır. 1 boyutlu n-gramlar “unigram”, 2 boyutlular “bigram” , 3 boyutlular “trigram”  olarak adlandırılır. 
	- X = “ Le chat est sur le tapis.”
	- Y1 = “The cat is on the mat.” ( insan kaynağı 1 ) 
	- Y2 = “ There is a cat on the mat.” ( insan kaynağı 2 ) 
	- Yine bu örnek üzerinden gidersek, makine çıktısı : “The cat the cat on the mat” olsun. Makine çıktısına ait bigramlar : <br><br>
  ![69.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/69.jpg) <br><br>
	- n-gram’ lar için değiştirilmiş precision hesapları ise şu şekildedir : <br><br>
  ![70.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/70.jpg) <br><br>
	- BLEU puanını oluşturmak için değiştirilmiş precision değerlerini de kullanırsak : 
		* Pn : n-gram’ larda Bleu skoru olsun,
		* Birleşik BLEU puanı : BP * exp( 1/n * sum(Pn ))
			- Örneğin 4 değeri için BLEU puanı : P1, P2, P3, P4 hesaplanır ve ortalaması alındıktan sonra exp hesabı yapılır. 
		* BP, kısa cezası anlamına gelen ceza değeridir. Bu değer kullanılmazsa, makine daha kısa çıktı verme eğiliminde olacaktır. <br><br>
  ![71.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/71.jpg) <br><br>
	- BLEU değeri, makine çevirisi ve resim alt yazısı gibi çeşitli sistemlerde kullanılmaktadır. <br><br> 

* Dikkat Modeli ( Attention Model Intuition ) : Dersin bu noktasına kadar kodlayıcı ve kod çözücüler için diziler kullanılmıştır. Bu noktadan sonra, daha iyi iyileştirmeler yapılabilmesi için “attention” tekniği açıklanacaktır. 
	- Uzun diziler sorunu : <br><br>
  ![72.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/72.jpg) <br><br>
	- Verilen bu örnekte, kodlayıcı bu uzun diziyi bir vektörde ezberlemesi ve kod çözücünün çeviriyi oluşturmak için bu vektörü işlemesi gerekmektedir.
	- Bir insan çevirisinde, bu tercüme için çeviriyi yapan kişi cümlenin tamamını okuyup, ezberleyip çevirmeye çalışmaz. Her seferinde bir bölümü çevirmeye çalışır. Makine çevirisinde bu ezberleme işi, uzun cümleler için performansı çok fazla düşürmektedir. Bu nedenle dkkat modelleri, her seferinde parça incelemesi yapan insan tercüman gibi bir işlem gerçekleştirir. Bu sayede daha uzun sekanslarda bile doğruluk önemli ölçüde artırılabilmektedir. Aşağıda mavi çizgi normal modele, yeşil ise dikkat mekanizmalı modele aittir. <br> <br>
  ![73.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/73.jpg) <br><br>
	- İlk başta dikkat modeli, makine çevirisi için geliştirilmiştir ancak daha sonra bilgisayar görüşü ve neural turing makinesi gibi diğer uygulamalar tarafından da kullanılmıştır. Dikkat modeli için kaynak gösterilen makale : https://arxiv.org/abs/1409.0473 
	- Dikkat modelinin anlatımına gelecek olursak : 
		* Kodlayıcının çift yönlü bir RNN olduğunu düşünelim, <br><br>
  ![74.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/74.jpg) <br><br>
		* Kodlayıcıya Fransızca bir cümle verilir ve girişi temsil eden bir vektör oluşturması beklenir. 
		* “Jane” in İngilizce çeviride oluşturulması için kod çözücü niteliğinde bir başka RNN kullanalım. Dikkat ağırlıkları, bir kelime üretilirken hangi kelimelerin gerekli olduunu belirtmek için kullanılır. Yani “Jane” oluşturmak için “jane ( Fransızca girdideki)”, “visite”, “l’ Afrique” ifadelerine bakılır. <br> 
  ![75.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/75.jpg) <br>
		* alpha<1,1>, alpha<1,2>, alpha<1,3> dikkat ağırlıkları ve S^<0>, S^<1>,... ise RNN’ in gizli durum aktivasyonlarını ifade etmektedir.  Bu noktada, herhangi bir kelimeyi oluşturmak için şu anda hangi kelimelere baktığımızı kontrol eden bir dizi dikkat ağırlığı kullanılacaktır. <br><br>
  ![76.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/76.jpg) <br><br>
* Dikkat Modeli : Dikkat modelini daha ayrıntılı inceleyelim. 
	- İlk olarak, Fransızca dilini kodlayan çift yönlü bir RNN’  imiz olsun. <br><br>
  ![77.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/77.jpg) <br><br>
	- a^<t’>, t2 zaman adımında her iki yöndeki aktivasyonları içermektedir. ( a^<t’> = ( a^<t’> forward, a^<t’> backward ) )
	- Çıktının a<t> içinde ne kadar bilgi araması gerektiğini gösteren, dikkat ağırlıkları kullanılarak hesaplanan bir c bağlamını kullanarak çıktıyı üretmek için tek yönlü bir RNN' imiz olsun. <br><br>
  ![78.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/78.jpg) <br><br>
	- Dizideki her öğe için dikkat ağırlıkları toplamı 1 olmalıdır. <br><br>
  ![79.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/79.jpg) <br><br>
	- c ise şu şekilde hesaplanır : <br><br>
  ![80.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/80.jpg) <br><br>
	- dikkat ağırlığı alpha^<t, t’ > hesaplanır. ( NOT : Yani alpha<t, t'> = y<t>'nin a<t'>'ye vermesi gereken dikkat miktarıdır. Mesela alfa, alpha^<1,1> , alpha^<1,2>, alpha^<1,3> için ilk üç kelimeye dikkat eder. ) 
	- Dikkat ağırlıkları toplamı 1 olacak şekilde yumuşatılır.  <br><br>
  ![81.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/81.jpg) <br><br>
	- Bu noktadan sonra e^<t, t’ > hesaplamasının yapılması gerekmektedir. Bu hesap için küçük bir sinir ağı kullanılır. ( Bu ağ genelde tek katmandan oluşur, çünkü bu katmanların artması, hesaplanacak değerin çok olmasından dolayı maliyeti artırır) <br><br>
  ![82.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/82.jpg) <br><br>
	- S^<t-1>, RNN’ in gizli surumu S’ dir. a^<t’> ise, çift yönlü RNN’ in aktivasyonunu ifade etmektedir. 
	- Bu algoritmanın maliyeti çok fazladır. 
	- Dikkat ağırlıklarının görselleştirilmiş hali aşağıda verilmiştir. <br><br>
  ![83.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/83.jpg) <br><br>
	<br><br>
* Konuşma Tanıma - Ses Verileri : 
* Konuşma tanıma : Konuşma tanımada X : ses klibi, Y : transkripttir. Bir ses klibinin görselleştirilmiş hali aşağıda verilmiştir. <br> <br> 
  ![84.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/84.jpg) <br><br>
	- Yatay eksen zamanı, dikey eksen hava basıncı değişikliklerini ifade etmektedir. 
	- Ses kaydı nedir ? : Bir mikrofon ile hava basıncındaki değişiklikler kaydedilir. Ses kaydı, bu kaydedilen hava basıncı değişikliklerini ölçen bir sayı dizisidir. 
	- Yukarıdaki ses kaydı görünümü için, insan kulağının algıladığına benzer bir spektogram bastırısak aşağıdaki gibi görünecektir. <br><br>
  ![85.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/85.jpg) <br><br>
	- Farklı renklerin yoğunluğu, enerji miktarını, farklı frekansları ifade etmektedir. 
	- Konuşma tanım aiçin, dikkat modeli kullanılarak doğru bir konuşma tanıma sistemi inşa edilebilmektedir. <br><br>
  ![86.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/86.jpg) <br><br>
	- Konuşma tanımada etkili olan bir diğer yöntem ise CTC’ dir. CTC’ yi açıklayacak olursak ; 
		* Y = “the quick brown fox” olsun ve RNN kullanılsın ( Verilen örnekte RNN tek yönlüdür ancak pratik uygulamalarda çift yönlü RNN kullanılır. ) <br><br>
  ![87.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/87.jpg) <br><br>
		* Dikkat edilirse RNN’ de giriş ve çıkış sayıları eşittir. Ancak konuşma tanıma uygulamaları genelde girişin çıkıştan büyük olması eğilimindedir. ( 100 Hz ses kayıtlarında 10 saniyelik ses, X ( 1000, ) verir. Bu 10 saniye için çıktılar 1000 karakter içermezler. Dolayısıyla girişler çıkış boyutundan daha büyüktür. ) 
		* CTC, RNN’ in şuna benzer bir çıktı vermesini sağlar : 
			- ttt_h_eee<SPC>____<SPC>qqq____ ( çıkış = the q )
			- Burada <SPC> boşluğu ifade etmektedir. 
			- CTC’ de ana kural, <SPC> ile ayrılmayan karakterlerin daraltılarak çıktıya aktarılmasıdır. Bu nedenle çıktı “the q” şeklindedir.
			- İlgili makale : https://dl.acm.org/doi/10.1145/1143844.1143891 

	- Bu noktada, hem dikkat modeli hem de CTC kullanımı, konuşma tanımayı oldukça etkili hale getirmektedir. 

* Trigger Word Detection (Tetikleyici kelime tespiti ) : Trigger Word ( tetikleyici kelime ) tespit sistemleri, algılanan bir kelime ile sistemin aktifleşmesini sağlar. Aşağıda bu sistemlere örnek verilmiştir. <br><br><br>
  ![88.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/88.jpg) <br><br>
	- Trigger Word sistemleri henüz gelişmekte olduğu için kabul görülen evrensel bir algoritma yoktur. Ancak, kullanılabilecek bir algoritma aşağıda verilmiştir. İlk olarak bir model oluşturulsun ; 
		* X : ses klibi
		* X işlenir ve spektogramı döndürülür. ( X^<1>, X^<2>, …X^<t> )
		* Y, 0 veya 1 olacaktır. 0, tetikleyici olmayan kelime, 1 ise tetikleyici kelimedir.
		* Model mimarisi şu şekildedir : <br><br>
  ![89.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/89.jpg) <br><br>
		* Ses klibindeki dikey çizgiler, tetikleyici kelimeden hemen sonraki anı temsil etmektedir. 
		* Bu modelin dezavantajı, çok dengesiz bir eğitim setine sahip olmasıdır. Eğitim seti çok fazla 0 ve az sayıda 1 içermektedir. Bu durumu düzeltmek için, algılanan her 1 den sonra birkaç kez geriye dönülür ve sabit bir süre içinde birden çok “1” değeri alınması sağlanır. Aşağıda bu duruma bir örnek verilmiştir. <br><br>
  ![90.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/90.jpg) <br><br><br><br>
* Transformer Ağlar : 
* Transformer Network Intuition : 
	- Günümüzde çokça kullanılan NLP ve bilgisayarlı görü algoritmaları, transformer ağlara dayanmaktadır. Transformer ağlar, diğer algoritmalara göre nispeten daha karmaşık sinir ağı mimarisine sahiptirler. 
	- Dersin bu noktasına RNN, LSTM ve GRU’ lar işlendi. 
		* Bu yapılar ile bilgi akışı üzerinde gelişmiş kontrol sağlanıken hesaplama karmaşıklıkları da artmıştır. Bu sistemlerde genel olarak, mevcut birimlerin hesabının yapılabilmesi için daha önce gelen tüm birimlerin çıktılarının hesaplanması gerekmektedir. Bu da darboğaza sebep olmaktadır. 

	- Transformer ağlar ; Hesaplamaların tüm girdi dizisi için paralel çalıştırılmasına izin vermektedir. 
		* Kelimeler soldan sağa tek tek işlenmez, girdi bir bütün olarak aynı anda alınabilir. ( Kaynak makale : https://arxiv.org/abs/1706.03762 ) 
		* Transformer : CNN işleme tarzı ile Dikkat temsillerini bir arada kullanır.  RNN her seferinde bir çıktıyı işleyebilir. Dikkat, kelimelerin çok zengin temsillerini hesaplayabilir. CNN, çok sayıda girdi alır ve bunların gösterimlerini paralel olarak hesaplar. 
	- Transformer Ağlarda kullanılan iki önemli başlık : 
		* Öz dikkat :  n kelime için n temsil paralel olarak  hesaplanır.
		* Çok başlı dikkat :  Öz dikkat için uygulanan döngüler, bu temsillerin birden çok versiyonunu oluşturur. 

* Öz Dikkat : 
	- Yine “Jane visite L’Afrique en September” örneği üzerinden gidilsin. 
	- Her kelime için elimizde : 
		* A(q, k, V) : bir kelimenin dikkat tabanlı vektör gösterimi olsun.
		* Her kelime için A^<1>, A^<2>
			- Normalde, bir kelimeyi temsil etmek için word embedding kullanılır.  Kullanılna kelimenin hangi bağlamda kullanıldığının ( coğrafi bir bahsetme mi ? , ilgi alanından mı bahsediliyor, tarihi olaylar mı ele alınmış ? vb) anlaşılabilmesi için çevredeki kelimelerin incelemesi yapılmalıdır. Bu yöntem önceki derslerde Dikkat mekanizmalarında uygulanmıştı. Ancak öz dikkat için bu temsiller, bir cümledeki beş kelime için paralel olarak hesaplanıyor. Yani daha önce açıklanan “cümledeki diğer kelimelerin incelenmesi” yöntemi, burada paralel olarak yapılıyor. 
		* A(q, k, V ) denklemi : <br><br>
  ![91.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/91.jpg) <br><br>
	- Burada her kelime için q^<i>, k^<i> ( key ) ve V^<i> (value ) şeklinde 3 değer vardır. 
		* q^<i> ; Kelimenin tanımlanabilmesi için sorulan soruları temsil eder 
		* k^<i> : kelimenin, soruya en uygun yanıtı verip vermediğini kontrol eder. ( k^<1> için “kişi”, “eylem” sonuçlarının alınması )
		* v^<i> : i' nin bu belirli kelimeyi A<i>  içinde temsil etmesi gerektiğini belirler.


	- Bir temsilin hesaplanması noktasında A^<3> şu şekilde çalışır : 
		* İlk olarak q, k, v değerleri hesaplanır : 
		* q^<3> = W^q * x^<3> ( W^q, öğrenilmiş bir ağırlık matrisidir.)
		* k^<3> = W^k * x^<3>
		* v^<3> = W^v * x^<3>
	- Daha sonra q^<3> ile diğer k^<1:5> arası iç çarpım yapılır. Burada amaç, bir kelimenin q sorularına ne kadar iyi cevap verebildiğini görmektir. İlerleyen bölümde ise elde edilen bu iç çarpım sonuçları üzerinde bir softmax hesaplanır. (Aşağıda verilen görsel üzerinde  q^<3> * k^<2>, en büyük değere sahiptir. ) 
	- Softmax sonucu alınan değer, v^<i> ile çarpılır ve çarpımlar toplanarak A^<3> değeri elde edilir. 
	- Anlatılan örnek aşağıda verilmiştir. <br><br>

  ![92.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/92.jpg) <br><br>
	- Yapılan bu işlem, dizideki bütün kelimeler için tekrarlanır. 
	- Sonuç olarak öz dikkat şu şekilde hesaplanır : 
	- Attention(q, k, v ) = softmax(q, dot(k.T) / sqrt(d_k)). <br><br>
* Çok Başlı Dikkat : 
	- Öz yineleme her çalıştırıldığında üzerinde durulan kelime head olarak alınır. 
	- Öz dikkat ile aynı şekilde [q, k, v] değerleri kullanılır, Dikkat(W^<q1,> * q,  W^<k1> * k, W<v1> * v ) değerleri hesaplanır. Her döngüde W^<q2> , W^<k2>, W<v2> şeklinde değerler güncellenir. 
	- Aşağıda verilen örnekte, farklı renkteki oklar, cümledeki farklı kelimeler için yapılan “head” hesaplarını göstermektedir. kırmızı ok = September, siyah = Jane vb şekilde bütün kelimeler(head) için yukarıda anlatılan işlem tamamlanır. Daha sonra elde edilen head değerleri bir araya getirilir. Bu sistem “çok başlı dikkat” olarak adlandırılır.  <br><br>
  ![93.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/93.jpg) <br><br>
	- Çok başlı dikkat şu şekilde hesaplanır : 
		* Multihead(q, k, v) = concat(heads).W0 <br><br><br>

* Transformer Ağlar : 
	- Trandformer ağların ana fikri : 
		* Gömme e değeri, q, k, ve v ile beraber bir çok başlı dikkate sahip kodlayıcıya beslenir. Ardından ileri beslemeli sinir ağına geçer. Bu kodlayıcı blok N kez tekrarlanır. 
		* Decoder tarafında ise : q matrisi, k ve v ile birleştirilir ve ikinci çok başlı dikkat bloğuna gönderilir. 
		* İlk bloktaki q, geçen süre boyunca oluşturulan kelimedir. Dizide oluşturulacak bir sonraki kelimenin ne olduğuna karar vermek için orijinal Fransızca kelimelerden k ve q ile birleştirilir. 
		* Son olarak, ikinci bloğun çıkışı İleri Beslemeli NN’ e beslenir ve dekoder bloğu da N kez tekrarlanır. Dekoder bloğunun çıktısı, sonraki en uygun İngilizce kelimenin oluşturulması için sonraki turda tekrar girişe beslenir. <br><br><br><br>
  ![94.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/94.jpg) <br><br><br>
* Transformer’ ı daha iyi hale getirmek için bazı teknikler : 
	1) Konumsal Kodlama ( Positional Encoding ) : Örneğin embedding word 4 değerli bir vektör olsun. Pozisyon vektörü p ile aynı boyutta bir pos vektörü oluşturulur. 4 değerli bir örnek üzerinde çalışıldığı için i 0:3 arası için değer alır. Elde edilen pos / (kelime_dağarcığındaki_kelime_sayısı)^< 2i / d >) değeri için sin/cos işlemleri uygulanır. Buradan alınan pozisyonel sonuç, dekoder’ a beslenir. 
	2) Dekoder beslemesinden sonra çok başlıklı dikkat modülleri arasında add & norm uygulanır. En son dekoder çıktısı ise sırasıyla bir lineer katmana ve softmax katmanına uygulanır. <br><br><br>

  ![95.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/95.jpg) <br><br>
* Not Defterlerinden Alınan Ekstralar 
	- Dikkat modülleri ile kullanılan modellerin gösterimleri : <br><br>

![96.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/96.jpg) <br><br>
![97.jpg](https://github.com/SeymaAtmaca/Deep-Learning-Specialization/blob/main/Sequence%20Models/images/97.jpg) <br>
	




  
  
  
  
  
  
  
