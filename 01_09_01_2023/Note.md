#### **1. C++ Diline Genel Bakış**

- **Popülerlik ve Gelecek:** C++, TIOBE Endeksi'ne göre dünyanın en popüler 3 programlama dilinden biridir ve 2022 yılında en büyük populerite artışını yaşayan dil olmuştur. "C++ ölüyor" gibi söylemler gerçeği yansıtmamaktadır; dil, kısa ve orta vadede önemini yitirmeyecektir.
- **Modern C++:** Kurs, "Modern C++" olarak adlandırılan 2011 standartları ve sonrasını temel almaktadır. Minimal taban C++17 standartları olacaktır, ancak C++20 ve C++23 standartlarındaki yeniliklere de değinilecektir. Modern C++ ile kod yazmak kolaylaşmış, üretilen kodlar daha verimli hale gelmiş ve hata yapma riski azalmıştır.
- **Tanım:** C++, C dilinin bir sürümü değildir; ayrı bir programlama dilidir. İsmi, C'nin üzerine eklemeler yapıldığı vurgusunu taşıyan bir espriden gelir (`++` C'deki artırma operatörüdür).
- **Multi-Paradigma Yaklaşımı:** C++'ın en önemli özelliği, "multi-paradigm" bir dil olmasıdır. Programcıyı tek bir programlama yaklaşımına (paradigmaya) zorlamaz. Prosedürel (procedural), nesne yönelimli (object-oriented), fonksiyonel (functional) ve jenerik (generic) programlama gibi farklı paradigmaları bir arada kullanma imkanı sunar.

#### **2. C ve C++ Arasındaki Uyumsuzluklar (İlk Bakış)**
- **Giriş:** C dilinde geçerli olan her kod, C++'ta geçerli olmayabilir. Bunun temel nedenlerinden biri, C++'ın C'ye göre çok daha katı bir tür kontrol sistemine sahip olmasıdır.
- **C'de Olan C++'da Olmayan Araçlar:** C99 standartlarıyla C diline eklenen bazı araçlar (örneğin; `Compound Literals`, `Restrict` anahtar sözcüğü, `Flexible Array Members`) C++'ta bulunmaz.
- **Fonksiyon Bildirimleri:**
- **Implicit Int:** C'de bir fonksiyonun geri dönüş türü belirtilmezse `int` olarak kabul edilir (`implicit int`). C++'ta bu durum bir `syntax` hatasıdır ve tür açıkça belirtilmelidir.
- **Boş Parametre Listesi:** C'de `func()` bildirimi, fonksiyonun parametreleri hakkında bilgi verilmediği anlamına gelirken, `func(void)` parametre almadığı anlamına gelir. C++'ta ise her iki bildirim de fonksiyonun parametre almadığı anlamına gelir ve aralarında bir fark yoktur.
- **Karakter Sabitlerinin Türü:** C dilinde `'A'` gibi karakter sabitlerinin türü `int`'tir. C++'da ise bu sabitlerin türü `char`'dır. Bu, iki dil arasındaki en önemli farklardan biridir.
- **String Literallerinin Türü:** C'de `"abc"` gibi string literalleri `char[]` (karakter dizisi) türündedir. C++'ta ise `const char[]` (sabit karakter dizisi) türündedir. Her iki dilde de string literallerini değiştirmeye çalışmak "tanımsız davranış" (undefined behavior) olarak kabul edilir.

#### **3. C++’ta C Öğelerinin Kullanımı ve Alternatifleri**

##### **3.1. C’deki Araçların C++’ta Kullanım Durumu**

- C++ dili, C’den daha kapsamlı ve güçlü araçlar sunar. Bu nedenle C’deki bazı yapıların **modern C++ uygulamalarında tercih edilmediği** görülür.
- C’deki her şeyi C++’ta kullanmak teknik olarak mümkün olsa da, **“kullanmak doğru mu?”** sorusu önemlidir.
	
###### **3.1.1. Ön İşlemci ve Makrolar**
- **C’de yaygın:** #define ile makro tanımlama.
- **C++’ta tercih edilmez.** Sebep: Makrolar tip denetimi yapmaz, hata ayıklaması zordur.
- **Alternatif:** const, constexpr, inline fonksiyonlar.

    **Örnek:**
```
	// Kötü kullanım - C tarzı
	#define PI 3.14
	
	// Doğru kullanım - C++ tarzı
	constexpr double PI = 3.14;
```

##### **3.2. Diziler (Arrays) ve Modern Alternatifleri**
###### **3.2.1. C Tarzı Dizi Kullanımı**

- C’de int arr[10]; gibi sabit uzunluklu diziler yaygındır.
- Bu diziler:
    - Bellek taşmalarına açık
    - Boyut bilgisini taşımaz
    - STL ile uyumsuzdur
    
###### **3.2.2 C++’ta Modern Alternatifler**

1. std::vector → Dinamik diziler
2. std::array → Sabit boyutlu ama güvenli diziler (C++11 sonrası)
3. std::string → char[] yerine metinler için
    
**Örnek:**
```
	// C tarzı
	char name[20] = "Cpp";
	
	// Modern C++
	std::string name = "Cpp";
```

##### **3.3. Null-Terminated Karakter Dizileri vs std::string**

###### **3.3.1. C’deki Karakter Dizileri**

- char[] dizileri null (\0) karakteriyle sonlandırılır.
    
- Hatalara açıktır:
    - strcpy, strcat, strlen gibi fonksiyonlar dikkatli kullanılmazsa **buffer overflow** riskleri doğurur.
    
###### **3.3.2. C++’ta std::string Kullanımı**
- Bellek yönetimi otomatik
- Kolay karşılaştırma, kopyalama, ekleme
- STL fonksiyonlarıyla uyumlu
    **Örnek:**
```
    std::string name = "Arden";
    name += " Ulaş"; 
```
#### **Derleyici ve Modern C++ Yaklaşımı ; Güvenlik ve Tip Denetimi**
- C++ derleyicisi:
    - Daha sıkı tip denetimi yapar.
    - Modern yapılarla hata yapmayı zorlaştırır.
- C’nin sunduğu bazı araçlar **C++’ta hem gereksiz hem de tehlikeli** hale gelir.

#### **3. Tanımsız Davranış ( Undefined Behavior )**
- **Tanım:**
    Standart tarafından tanımlanmamış, gerçekleştiğinde programın sonucu öngörülemez hale gelir. Derleyici bu durumda herhangi bir davranış sergileyebilir:
	    
    - Program çöker
    - Yanlış sonuç verir        
    - Hatta “hiçbir şey yapmaz” gibi görünse bile arka planda zarar verebilir
	    
- **Örnekler:**
```
int x = 5 / 0;             // Tanımsız davranış: Sıfıra bölme

int arr[3] = {1, 2, 3};

int y = arr[5];            // Tanımsız davranış: Diziyi sınır dışı okumak
```
    
- **C ve C++ Farkı:**
> “C’de undefined behavior olan her şey C++’ta da undefined behavior mıdır?”
	Cevap: Hayır. Bazı UB durumları sadece birinde geçerli olabilir. Örneğin C++ bazı UB durumlarını tanımlı hale getirebilir veya farklı kurallar koyabilir.

#### **4. Belirtilmemiş Davranış ( Unspecified Behavior )**

- **Tanım:**
    Standart bazı davranışları bilinçli olarak **belirtmez**. Ancak bu davranışlar UB gibi tehlikeli değildir. Yani sonuçlardan biri seçilir, ama hangi biri olduğu garanti edilmez.
    
- **Örnek:**
```
	int x = f1() + f2(); // f1 mi önce çağrılır, f2 mi? Belirtilmemiş davranış.
```
- **Not:**
    
    - **Kötü müdür?** Hayır.
    - Yine de **tahmin edilemez** ve farklı derleyiciler farklı çalıştırabilir.
    - Optimizasyonları etkileyebilir.

#### **5.Uygulama Tanımı( Implementation Defined )**
- **Tanım:**
    
    Standart, davranışı açıkça **derleyiciye bırakır** ama **belgelemek zorundadır.** Yani derleyici bu durumda ne yaptığını dokümantasyonunda belirtmelidir.
    
- **Örnekler:**
    
    - char türünün signed mı unsigned mı olduğu
    - Sağdan sola mı soldan sağa mı değer atandığı gibi detaylar
    
- **Örnek:**
```
char c = 255;  // Bazı derleyiciler signed olarak 255'i -1 yapar
```

*NOT:  “Implementation defined behavior, unspecified behavior’ın alt kümesidir. Ancak her unspecified behavior implementation defined değildir.”*

|**Davranış Türü**|**Tanımı**|**Tehlike Durumu**|**Derleyici Belirtir mi?**|
|---|---|---|---|
|**Undefined Behavior (UB)**|Standart dışı, sonuç belirsiz|Yüksek risk|Belirtmek zorunda değil|
|**Unspecified Behavior**|Sonuçlardan biri, ama hangisi belirsiz|Orta risk|Belirtmek zorunda değil|
|**Implementation Defined**|Derleyiciye bağlı, belge zorunlu|Kontrollü|Belirtmek zorunda|