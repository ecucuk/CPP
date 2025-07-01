# **C++ DERS NOTLARI – 3. GÜN (13 OCAK 2023)**

**Konu:** C ve C++’ta Kullanıcı Tanımlı Türler (User Defined Types)

**Düzey:** Başlangıç-Orta

**Hedef:** struct, enum, typedef, union ve modern C++ yapılarının farklarını anlamak

---

## **1. Giriş: “User Defined Types” Nedir?**

### **1.1 Tanım:**

**User Defined Types (UDT)**, programcının kendi veri türlerini tanımlamasını sağlayan yapılardır. Bunlar:

- struct
    
- union
    
- enum
    
- typedef
    
- class _(C++’a özel)_
    

  
### **1.2 Neden Kullanılır?**

- Daha anlamlı ve organize veri yapıları tanımlamak
    
- Çoklu değişkenleri tek yapıda toplamak
    
- Daha okunabilir kod yazmak
    

> **Önemli:** UDT’ler C++’ta daha güçlüdür çünkü **fonksiyon, erişim belirleyici, constructor/destructor gibi özelliklerle zenginleştirilmiştir.**

---

## **2. struct – Yapı Tanımları**

### **2.1 C Dilinde struct**

```
struct Ogrenci {
    char isim[30];
    int yas;
    float ortalama;
};

struct Ogrenci ali;
```

- Veri gruplarını tek çatı altında toplar.
    
- C’de fonksiyon içeremez.
    
- struct anahtar kelimesi her kullanımda yazılmalıdır.
    

### **2.2 C++ Dilinde struct**

```
struct Ogrenci {
    string isim;
    int yas;
    float ortalama;

    void bilgiYazdir() {
        cout << isim << " " << yas << " " << ortalama << endl;
    }
};
```

- C++’ta struct, **fonksiyon barındırabilir**.
    
- C++’ta struct’lar varsayılan olarak **public** erişimlidir.
    

  
> **Yaygın Hata:** C’de struct Ogrenci yazmak zorunlu; C++’ta sadece Ogrenci yeterlidir.

---

## **3. typedef – Tür Takma Adı**

### **3.1 Temel Kullanım**

```
typedef unsigned int uint;
uint x = 100;
```

- Uzun türleri kısaltmak için kullanılır.
    
- C’de yaygındır, C++’ta yerine using tercih edilir.
    

  

### **3.2 Modern C++’ta Alternatif**

```
using uint = unsigned int;
```

> **İpucu:** using daha okunabilir ve şablonlarla (template) daha iyi uyumludur.

---

## **4. enum – Sabitler Listesi**

  

### **4.1 C Stili enum**

```
enum Renk {Kirmizi, Yesil, Mavi};
Renk r = Mavi;
```

- Sıralı sabitler tanımlar.
    
- Varsayılan olarak 0’dan başlar.
    

  

### **4.2 C++11 enum class**

```
enum class Renk {Kirmizi, Yesil, Mavi};
Renk r = Renk::Mavi;
```

- **Scope (alan) güvenliği sağlar**
    
- İsim çakışmalarını engeller
    

> enum class kullanırken Renk::Yesil gibi tam adla erişim gerekir.

---

## **5. union – Bellek Paylaşımı**

### **5.1 Tanım:**

```
union Veri {
    int tamsayi;
    float ondalikli;
};
```

- Aynı belleği paylaşan farklı türler
    
- Aynı anda sadece bir üye aktif olabilir
    

  

### **5.2 Kullanım Durumu:**

```
union Veri v;
v.tamsayi = 10;
cout << v.tamsayi;
```

> Son atanan alan dışındakiler bozulur.

---

## **6. class – C++’ın Temel Gücü**

```
class Ogrenci {
private:
    string isim;
    int yas;

public:
    Ogrenci(string ad, int y) : isim(ad), yas(y) {}
    void yazdir() {
        cout << isim << " - " << yas << endl;
    }
};
```

- struct’tan farkı: **varsayılan erişim seviyesi private**
    
- Kapsülleme, miras alma ve çok biçimlilik gibi OOP özellikleri içerir.
    

---

## **7. Kıyas Tablosu: C vs C++**

|**Yapı**|**C Dilinde**|**C++ Dilinde**|
|---|---|---|
|struct|Sadece veri taşır|Fonksiyon barındırabilir|
|typedef|Var|using ile modernleşti|
|enum|Global alan|enum class ile scope güvenliği|
|union|Aynı|Aynı|
|class|Yok|Nesne yönelimli programlamanın temeli|