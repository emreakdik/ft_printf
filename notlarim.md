Gerekli dönüşümler hakkında kısa açıklamalar:
- %c tek bir karakter yazdırır.
- %s bir karakter dizisi yazdırır.
- %p Void * pointer argümanını hexadecimal biçiminde yazdırır. 
- %d 10 tabanında decimal sayı yazdırır. 
- %i 10 tabanında tam sayı yazdırır.
- %u 10 tabanında işaretsiz decimal sayı yazdırır.
- %x hexadecimal sayıyı (16 tabanında) küçük harfler ile yazdırır. 
- %X hexadecimal sayıyı (16 tabanında) büyük harfler ile yazdırır. 
- %% yüzde işareti yazdırır.

## **va_list**

  

-   Bir fonksiyonun sinirsiz arguman alabilmesi icin kullanilir.
    
-   Bir fonksiyonun sinirsiz parametre aldigini belirtmek icin kendi argumanlarindan sonra '...' koyuyoruz. int topla(int miktar, ...);
    
-   va_start makrosu iki arguman alir. Birincisi argumanlardir, ikincisi ise fonksiyonun hangi degiskenden sonra sinirsiz arguman almaya baslayacagini gosterir.
    
-   va_arg, ilk parametre olarak islem yapilacak va_list'i aliyor. Va_arg her cagirildiginda bir sonraki indeks'i (argumani) alir. Ornegin argumanlarin 22,33,44 oldugunu dusunelim. var_arg ilk cagirildiginda 22, ikinci cagirildiginda 33'u ceker. Ikinci aldigi parametre ise iceriden alinacak olan degerin hangi veri tipinde alinacagina karar verir.
    
-   va_end ile arguman kullanimini sonlandirip, temizlik islemini yapariz. Fakat daha sonra argumanlara ihtiyacimiz olursa, tekrar start verebiliriz.
    
## Bool Nedir?

C dilinde, bool türü bir değişkenin değerinin true (doğru) veya false (yanlış) olduğunu belirtmek için kullanılır. Örneğin, bir değişkenin değerinin doğru veya yanlış olduğunu belirtmek için bool türü kullanılabilir.

Örnek olarak, aşağıdaki kod bloğunda bool türünde bir değişken oluşturulur ve değerine true ataması yapılır:

```c
    #include <stdbool.h>
    
    int main(void) {
        bool flag = true;
        return 0;
    }
```

 Not: C dilinde bool türü `stdbool.h` kütüphanesinin bir parçasıdır ve bu kütüphane C dilinde bool türünün kullanımını sağlar.
