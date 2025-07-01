# **C++ DERS NOTLARI – 2. GÜN (11 OCAK 2023)**
---

## **1. Giriş: C++ Yolculuğuna Başlarken**

- **Motivasyon:** “Tek dil, tek sentaks, tek amaç” → C++ öğrenmek.
    
- Katılımcılar çoğunlukla **C bilen** kişiler.
    
- Dersin amacı: **C++’ın C’den farklarını ve temellerini anlamak**.
    

---

## **2. C ile C++ Arasındaki Farklar**

### **2.1 Temel Farklar**

- C bir **yapısal (procedural)** dil.
    
- C++ ise **çok paradigmalı**: Hem prosedürel hem nesne yönelimli programlamayı destekler.
    
- C++ daha fazla tür kontrolü ve güvenlik sunar.
    

  

### **2.2 Incompatible Yapılar**

- C++’ta bazı C söz dizimleri geçersizdir.
    
- Örnek: C’de malloc kullanılırken, C++’ta new/delete kullanılır.
    

---

## **3. C++ Temel Program Yapısı**

```
#include <iostream>
using namespace std;

int main() {
    cout << "Merhaba, C++!" << endl;
    return 0;
}
```

### **Açıklamalar:**

- #include <iostream> → Giriş/çıkış işlemleri için.
    
- using namespace std → std::cout yerine sadece cout kullanmak için.
    
- main() fonksiyonu, programın çalışmaya başladığı yerdir.
    

---

## **4. Değişkenler ve Veri Türleri**

### **4.1 Temel Veri Türleri:**

|**Veri Türü**|**Açıklama**|
|---|---|
|int|Tam sayılar|
|float|Ondalıklı sayılar|
|char|Tek karakter|
|bool|Doğru/yanlış|

### **4.2 Örnek:**

```
int sayi = 10;
float pi = 3.14;
char karakter = 'A';
bool aktif = true;
```

> **Kritik Not:** Değişkenler kullanılmadan önce tanımlanmalı ve tür belirtilmeli.

---

## **5. Girdi Alma (`cin`)**

```
int yas;
cout << "Yaşınızı giriniz: ";
cin >> yas;
```

- cin → Klavyeden veri alır.
    
- >> → Veri yönlendirme operatörü.
    
- Birden fazla değişken: cin >> a >> b;
    

---

## **6. Karar Yapıları ( **if, else if , else** )**

```
if (yas >= 18) {
    cout << "Reşitsiniz.";
} else {
    cout << "Reşit değilsiniz.";
}
```

- Koşul doğruysa if içindeki blok çalışır.
    
- else if ile çoklu kontrol yapılabilir.
    

  

### **Karşılaştırma Operatörleri:**

|**Operatör**|**Açıklama**|
|---|---|
|==|Eşittir|
|!=|Eşit değil|
|>|Büyüktür|
|<|Küçüktür|
|>=|Büyük eşittir|
|<=|Küçük eşittir|

---

## **7. Döngüler (Loops)**

### **7.1 for Döngüsü**

```
for (int i = 0; i < 5; i++) {
    cout << i << endl;
}
```

### **7.2 while Döngüsü**

```
int i = 0;
while (i < 5) {
    cout << i << endl;
    i++;
}
```

### **7.3 do-while Döngüsü**

```
int i = 0;
do {
    cout << i << endl;
    i++;
} while (i < 5);
```

> **Kritik Fark:** do-while döngüsü koşul yanlış olsa bile **en az bir kez çalışır**.

---

## **8. Fonksiyonlar**

### **8.1 Temel Fonksiyon Tanımı**

```
int topla(int a, int b) {
    return a + b;
}
```

### **8.2 Kullanımı**

```
int sonuc = topla(3, 5);
cout << "Toplam: " << sonuc;
```

> **Fonksiyonlar**, kodu modülerleştirir, tekrar kullanılabilirlik sağlar.

---

## **9. Diziler (Arrays)**

```
int sayilar[5] = {1, 2, 3, 4, 5};
for (int i = 0; i < 5; i++) {
    cout << sayilar[i] << " ";
}
```

- **0’dan başlar.** sayilar[0] → 1
    
- **Sabit uzunluklu** yapıdır. Dinamik dizi için vector kullanılır (ileride işlenecek).
    

---

## **10. Bonus: switch-case Yapısı**

```
int secim;
cin >> secim;

switch (secim) {
    case 1: cout << "Bir"; break;
    case 2: cout << "İki"; break;
    default: cout << "Bilinmeyen"; break;
}
```

- switch → Çoklu durum kontrolü için kullanılır.
    
- break → Aksi takdirde case’ler zincirleme çalışır.
    

---

## **11. C++’ta Sık Yapılan Hatalar**

- = ile == karıştırmak → atama vs karşılaştırma
    
- cin sonrası getline çalışmaması → cin.ignore() kullan
    
- Dizinin sınırlarını aşmak (out-of-bounds)
    
- main() fonksiyonunda return 0; unutmak
    

---

## **12. Derleyici ve IDE Önerileri**

|**Araç**|**Açıklama**|
|---|---|
|g++|GNU C++ derleyicisi|
|VS Code|Hafif IDE, C++ eklentili|
|CLion|JetBrains IDE, gelişmiş|
|Qt Creator|GUI ve C++ için ideal|
|OnlineGDB|Çevrimiçi C++ derleyici|
