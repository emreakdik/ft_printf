Gerekli dönüşümler hakkında kısa açıklamalar:
- **%c** tek bir karakter yazdırır.
- **%s** bir karakter dizisi yazdırır.
- **%p** Void * pointer argümanını hexadecimal biçiminde yazdırır. 
- **%d** 10 tabanında decimal sayı yazdırır. 
- **%i** 10 tabanında tam sayı yazdırır.
- **%u** 10 tabanında işaretsiz decimal sayı yazdırır.
- **%x** hexadecimal sayıyı (16 tabanında) küçük harfler ile yazdırır. 
- **%X** hexadecimal sayıyı (16 tabanında) büyük harfler ile yazdırır. 
- **%%** yüzde işareti yazdırır.

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

## write(1, &"0123456789"[a % 10], 1);

**write()** fonksiyonu, bir veriyi standart çıktıya yazar. Bu fonksiyon, üç parametre alır:

**int fd:** Veriyi yazılacağı dosya tanımlayıcısı. Burada, 1 kullanılmıştır ve bu, standart çıktıyı (ekranı) ifade eder.

**const void *buf:** Yazılacak veri. Burada, &"0123456789"[a % 10] ifadesi kullanılmıştır. Bu ifade, "0123456789" dizisinin a % 10 indeksine göre elemanının adresini verir. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade "4" karakterinin adresini verir.

**size_t count:** Yazılacak verinin boyutu. Burada, 1 kullanılmıştır ve bu, yalnızca bir karakter yazılacağını ifade eder. Bu ifade, değişken a'nın mod 10 (yani son basamağı) ile işaretli rakamı yazar. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade 4 rakamını yazar.

----------------

**buf parametresi,** yazılacak verinin adresini belirtir. Bu parametre, bir void * (gösterici) türündedir ve yazılacak verinin adresini içerebilir. Örneğin, bir karakter dizisi için kullanılabilecek bir ifade &"hello" şeklinde olabilir ve bu ifade, "hello" dizisinin adresini verir.

Bu kod bloğunda, &"0123456789"[a % 10] ifadesi kullanılmıştır ve bu ifade, "0123456789" dizisinin a % 10 indeksine göre elemanının adresini verir. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade "4" karakterinin adresini verir.

Bu ifade, write() fonksiyonunun buf parametresine geçirilerek, standart çıktıya yazdırılır. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade write(1, &"4", 1) şeklinde kullanılır ve 4 rakamı ekrana yazdırılır.*

## Recursive'ler nasil isliyor?

Ornek olarak 16lik bir bicimi alalim.

```c
if (a >= 16)
		ret += ft_hex(a / 16, c);
	if (c == 'X')
		write(1, &"0123456789ABCDEF"[a % 16], 1);
```
a degiskeni recursive ile 16'ya bolunerek fonksiyona tekrar gonderiliyor. a degiskeni 16'dan kucuk oldugunda bu dongu duruyor. En kucuk 16 katin mod karsiligini bulup standart ciktiya eklediginde recursive geriye dogru sarmaya (tekrar recursive'in oldugu satira girmeden asagidan devam ediyor) basliyor ve cikti tamamlaniyor.

## Neden (ret + 1)?

ret değişkeni, a 16'dan küçük olana kadar yapılan özyinelemeli çağrıların sayısını tutar. Bu değişken, her özyinelemeli çağrıda 1 arttırılır.

Sonuç olarak, ret değişkeni, a'yı hexadecimal temsilleştirmek için kaç kez özyinelemeli çağrı yapıldığını gösterir. Bu nedenle, ret değişkenine 1 eklenir ve ret + 1 değeri döndürülür. Bu, standart çıktıya yazılan karakterlerin toplam sayısını verir.