XSS A�IKLARI 

Php'de t�m girdiler ��pheli olarak de�erlendirilmeli ve xss a��klar�ndan korunmak i�in girdilerin kontrol edilmesi gerekir. Xss a��klar� kullan�can gelen bilgilerin i�ine gizlenen kod par�alar�d�r ve bunlar html format�ndad�r.

Bu nedenle girdilerden html etiketlerini temizlemek gerekir.

Bunun i�in komutumuz htmlspecialchars

��yle bir fonksiyon i�imizi g�recektir.
```



function temizle($data) {
    if (is_array($data)) {
        foreach ($data as $key => $value) {
        unset($data[$key]);
        $data[temizle($key)] = temizle($value);
        }
    } else {
        $data = htmlspecialchars($data, ENT_COMPAT);
    }
    return $data;
}

temizle($_GET['adi']);

```
Daha geli�mi� bir ��z�m i�in
https://gist.github.com/mbijon/1098477