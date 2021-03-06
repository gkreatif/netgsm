
# Netgsm Laravel Santral ve Sms Paketi

Hakkında
====================

Netgsm Laravel Santral ve Sms Paketi

Kullanımı
====================

> Laravel 5.*

 **Kurmak için :** 
```
composer require brkphp/netgsm
```
- App.php Dosyasına Provider olarak ekleyiniz : 
``` 
Brkphp\Netgsm\NetgsmServiceProvider::class,
```
- App.php Dosyasına Aliases olarak ekleyiniz : 
``` 
'Netgsm' => Brkphp\Netgsm\Facade\Netgsm::class,
```
 
 Ayarları Yayınlamak için : 
```
php artisan vendor:publish 
```

 Ayarları Yapmak için  : 
```
Config/netgsm.php içinde sisteme giriş yaparken kullandığınız bilgileri giriniz.
```


Sms Örnekleri
====================
**Sms Göndermek için** 

```
    $new = new \Brkphp\Netgsm\Sms();
    $new->message('deneme mesaj');
    $new->phone('0123456789');
    return $new->send();
```

Santral Örnekleri
====================

**Bugünün Kayıtlarını çekmek için** 

```
$new = new \Brkphp\Netgsm\Santral();
return $new->dateQuery();
```


>Sadece dateQuery fonkisyonunu çağırırsanız , bugünün kayıtlarını çekecektir.


**Tarih Bazlı Kayıtları çekmek için** 

```
$new = new \Brkphp\Netgsm\Santral();
$new->startDate(250820170000);
$new->stopDate(270820172359);
return $new->dateQuery();
```


>Tarihler date('dmYHi') formatında olmalıdır.


**Telefon Numarası ile Kayıtları çekmek için** 

```
$new = new \Brkphp\Netgsm\Santral();
$new->phone(123456789);
$new->phone(987654321);
return $new->sendQuery();
```


**Uniqid ile Kayıtları çekmek için** 

```
$new = new \Brkphp\Netgsm\Santral();
$new->uniqId(123456789);
$new->uniqId(987654321);
return $new->sendQuery();
```
İleri Seviye
====================
Herhangi bir ekstra veri göndermek isterseniz aşağıdaki fonksiyonları kullanabilirsiniz sms ve santral iki sınıftada kullanılabilir.

```
$new->addHeadParameter('key','value')
$new->addBodyParameter('key','value')
```

> Parametreler ile ilgili detaylı bilgi Netgsm Api Dökümanında bulunmaktadır. 
> [Net Gsm Api](https://www.netgsm.com.tr/Dokuman/sanal-santral.asp "Net Gsm Api")
