XSS AÇIKLARI 

Php'de tüm girdiler þüpheli olarak deðerlendirilmeli ve xss açýklarýndan korunmak için girdilerin kontrol edilmesi gerekir. Xss açýklarý kullanýcan gelen bilgilerin içine gizlenen kod parçalarýdýr ve bunlar html formatýndadýr.

Bu nedenle girdilerden html etiketlerini temizlemek gerekir.

Bunun için komutumuz htmlspecialchars

Þöyle bir fonksiyon iþimizi görecektir.
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
Daha geliþmiþ bir çözüm için
https://gist.github.com/mbijon/1098477