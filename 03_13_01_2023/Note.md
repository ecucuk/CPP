# **C++ DERS NOTLARI – 3. GÜN (13 OCAK 2023)**

  

**Konu:** Kullanıcı Tanımlı Türler (User Defined Types – UDT)

**Kapsam:** C ve C++’ta struct, union, enum, typedef, enum class, sınıflar ve tür sistemi farkları

**Hedef Kitle:** C bilen ama C++’ın farklılıklarını derinlemesine öğrenmek isteyenler

---

## **1. Giriş: Tür Sistemine Genel Bakış**

### **1.1 Derse Başlangıç**

- Ders 13 Ocak 2023, Cuma günü saat 19:30’da başlıyor.
    
- Eğitmen önceki derslerde yaşadığı sağlık sorununu açıklıyor ve bugünkü dersin daha performanslı geçeceğini belirtiyor.


### **1.2 Temel Ayrım: Basic vs User Defined Types**

#### **Önemli:**

C/C++’ta türler 2 ana kategoriye ayrılır:

- **Basic Types (Built-in, Primitive, Fundamental Types):**
    
    Örnek: int, float, char, bool
    
- **User Defined Types (UDT):**
    
    Programcı tarafından tanımlanır. C’de 3 temel UDT aracı vardır:
    
    - struct
        
    - union
        
    - enum
        
    

### **1.3 C++’ta Bu Yapıların Gelişimi**

- C++’ta struct, union, enum hala geçerlidir.
    
- Ancak C++’ta struct artık bir tür sınıftır (class).
    
    > C++’ta struct → bir sınıfın özel biçimidir. Fonksiyon, erişim belirleyici içerebilir.
    

---

## **2. struct – Yapı Tanımları**

### **2.1 C Stili Struct**

```
struct Ogrenci {
    char isim[30];
    int yas;
};

struct Ogrenci ali;
```

- C’de fonksiyon içermez.
    
- Her kullanımda struct anahtar sözcüğü gerekir.
    
- Ogrenci burada bir “**structure tag**” olarak adlandırılır.
    

#### **Sık Hata:**

```
Ogrenci ali; // C’de geçersiz
```

> Çözüm: typedef ile alias verilmeli veya her kullanımda struct yazılmalı.

---

### **2.2 C++ Stili Struct**

```
struct Ogrenci {
    std::string isim;
    int yas;

    void yazdir() {
        std::cout << isim << " " << yas << std::endl;
    }
};

Ogrenci ali = {"Ahmet", 21};
ali.yazdir();
```

#### **Farklılıklar:**

- C++’ta struct içinde fonksiyonlar tanımlanabilir.
    
- struct üyeleri varsayılan olarak **public** olur.
    

> C++’ta struct ≈ class, ancak class’ta default erişim private’tır.

---

## **3. enum – Sabit Gruplar**

### **3.1 C Stili Enum**

```
enum Renk { KIRMIZI, YESIL, MAVI };
Renk r = MAVI;
```

- Sayısal değerler 0’dan başlar.
    
- Global isim alanında yer alır.
    

### **3.2 C++11 ile Gelen** 

### **enum class**

```
enum class Renk { KIRMIZI, YESIL, MAVI };
Renk r = Renk::YESIL;
```

#### **Avantajları:**

- Tip güvenliği (type-safe)
    
- Scope izolasyonu (YESIL yerine Renk::YESIL)
    

  

> **Modern C++ için önerilen kullanım enum class’tır.**

---

## **4. union – Ortak Bellek Alanı**

```
union Veri {
    int i;
    float f;
};
```

- Aynı belleği paylaşan farklı tipler
    
- Aynı anda **sadece bir** alan anlamlı olur
    

#### **Kullanım:**

```
Veri v;
v.i = 42;
printf("%d", v.i);
```

> Son atanan alan dışındakiler bozulur. union’lar bellek tasarrufu için kullanılır.

---

## **🔁 5. typedef – Tür Takma Adı**

### **5.1 Geleneksel C Kullanımı:**

```
typedef unsigned int uint;
uint x = 10;
```

### **5.2 Modern C++’ta using**

```
using uint = unsigned int;
```

#### **Not:**

- typedef geriye dönük uyumluluk için hala kullanılır.
    
- using, daha okunabilir ve template uyumludur.
    

---

## **6. Kapsayıcı Bakış: C++ Tür Sistemi**

### **6.1 Sınıflar ve Struct’lar**

```
class Ogrenci {
private:
    string isim;
public:
    void setIsim(string ad) { isim = ad; }
};
```

- class: varsayılan private
    
- struct: varsayılan public
    
### **6.2 UDT’lerin Birbirine Dönüşümü**

```
typedef struct {
    int id;
    float gpa;
} Kayit;

Kayit ogr1 = {123, 3.5};
```

> C’de typedef struct {...} tarzı kullanılırken, C++’ta doğrudan struct yetebilir.

---

## **7. C vs C++ – UDT Farkları Tablosu**

|**Özellik**|**C**|**C++**|
|---|---|---|
|struct|Sadece veri taşır|Fonksiyon barındırır|
|union|Aynı|Aynı (ama class’larla birlikte kullanılır)|
|enum|Global alan|enum class ile scope güvenliği|
|typedef|Var|using tercih edilir|
|class|Yok|OOP için temel yapı|

---

## **8. Sık Yapılan Hatalar ve Uyarılar**

- typedef struct sonrası struct yazmayı unutmak
    
- C++’ta enum ile enum class’ı karıştırmak
    
- union içinde birden fazla alana aynı anda erişmeye çalışmak
    
- class içinde public/private erişim belirteçlerini unutmak
    

---

## **9.Özet**

- User Defined Types, C++’ın güçlü tür sisteminin temelini oluşturur.
    
- struct, union, enum, typedef C’den miras alınmış, ancak C++’ta daha güçlü ve güvenlidir.
    
- Modern C++’ta mümkün olduğunca:
    
    - using kullanın
        
    - enum class tercih edin
        
    - struct yerine class kullanarak erişim kontrolü sağlayın
        
    

---

## **10. Derinlemesine enum ve enum class Karşılaştırması**

Eğitmen bu bölümde enum ve enum class yapılarını gerçek uygulama senaryoları üzerinden daha da detaylandırıyor.

### **10.1 enum Tanımı ve Tehlikeleri**

```
enum Gun { Pazartesi, Sali, Carsamba };
enum Renk { Kirmizi, Sari, Mavi };

Gun g = Pazartesi;
Renk r = Sari;
```

Bu kodda Gun ve Renk farklı enum’lar olmasına rağmen, aslında aynı isim alanında yer alırlar ve **birbirleriyle karışabilir**:

```
if (g == Sari) // Geçerli ama mantıksız bir karşılaştırma!
```

> **Kritik Sorun:** Tip güvenliği yoktur. Farklı enum türleri birbirine atanabilir veya karşılaştırılabilir.

---

### **10.2 enum class ile Çözüm**

```
enum class Gun { Pazartesi, Sali, Carsamba };
enum class Renk { Kirmizi, Sari, Mavi };

Gun g = Gun::Pazartesi;
Renk r = Renk::Sari;
```

> Artık g == r gibi karşılaştırmalar **geçersizdir**. Derleyici hata verir.

> Bu da kodun **güvenliğini ve okunabilirliğini artırır**.

---

## **11. Bit Alanları (Bitfields) – Yapı İçinde Bit Seviyesinde Kontrol**

C/C++’ta bellekten tasarruf etmek için struct içinde **bit alanları** tanımlanabilir:

```
struct Ayarlar {
    unsigned int wifi : 1;
    unsigned int bluetooth : 1;
    unsigned int gps : 1;
};
```

Bu yapıdaki her alan sadece 1 bit yer kaplar.

### **Örnek:**

```
Ayarlar cihaz;
cihaz.wifi = 1;
cihaz.bluetooth = 0;
cihaz.gps = 1;
```

> Bu yöntem özellikle **gömülü sistemlerde** bellekten tasarruf için kullanılır.

---

## **12. Eğitmen Notları ve İpuçları**

### **12.1 Sınavlar ve Geri Bildirim**

- Eğitmen, öğrencilerin derslere düzenli katılmasının öneminden bahsediyor.
    
- “Yüz yüze eğitim” ile çevrim içi eğitimin farklarını vurguluyor.
    

### **12.2 Öğrenme Yöntemi**

- Öğrencinin kendi bilgisayarında deneme yapması gerektiği tekrar vurgulanıyor.
    
- enum, typedef, struct, union gibi yapıları gerçek kod örnekleriyle test etmek teşvik ediliyor.
    

---

## **13. Sık Yapılan Hatalar ve Uygulama Notları**

|**Hata**|**Açıklama**|
|---|---|
|struct yerine class unutmak|Access modifier hataları oluşabilir|
|enum kullanırken çakışan isimler|Tip güvenliği ihlali|
|typedef yerine hala eski struct kullanımı|Modern C++ konvansiyonlarına aykırı|
|union’da aynı anda birden fazla alanı kullanmak|Bellek tutarsızlığı|

---

## **14. Genel Özet ve Öneriler**

- **C kullanıcıları için:** Bu yapılar tanıdık ama C++’ta daha güçlü ve kullanışlı.
    
- struct ve class arasındaki farklara dikkat et.
    
- enum class kullanarak kod güvenliğini artır.
    
- Gelişmiş tür sistemini using, typedef, union, bitfield gibi araçlarla güçlendir.
