# MEVLANA

## TR:
#### MEVLANA bir XHR/AJAX önleyicisi ve düzenleyicisidir.

### Özellikleri

* XHR/AJAX isteklerini ve yanıtlarını iptal edebilir veya değiştirebilir
* addEventListener ve removeEventListener ile uyumludur

### Örnek

Bu örnekte, sunucuya giden isteğin urlsi "pqo.php" içeriyorsa isteği iptal eder.

``` javascript
MEVLANA.before(function(request) {
  if(request.url.match(/pqo.php$/)){
    request.abort();
  }
});
```

## Tarayıcı desteği
Chrome, Firefox ve Safari üzerinde test edildi.

## Dikkat

:warning: MEVLANA'yı öncelikle include ettiğinizden emin olun. (Diğer kütüphaneler MEVLANA ile `XMLHttpRequest` konusunda çakışabilir.)

## API

### `MEVLANA.before(handler(request[, callback])[, index])`

XHR isteğini gönderilmeden önce düzenleyebilir veya iptal edebilir.

`handler`'ın asenkron olması için, opsiyonel olan `callback` fonksiyonunu eklemeyi unutmayın.

Sahte bir cevap döndürmek için, sadece `response` objesini `return` veya `callback()` kullanarak döndürün.

### `MEVLANA.after(handler(request, response[, callback]) [, index])`

Sunucudan gelen isteği XHR almadan önce düzenler.

`handler`'ın asenkron olması için, opsiyonel olan `callback` fonksiyonunu eklemeyi unutmayın.

### `MEVLANA.enable()`

MEVLANA'yı etkinleştirir ve MEVLANA varsayılan olarak etkindir. Yerel `XMLHttpRequest` classını modifiye eder.

### `MEVLANA.disable()`

MEVLANA'yı etkisizleştirir. `XMLHttpRequest` classını tekrardan eski haline döndürür.

---

### `request` Objesi

* `method` (String) (*<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#open()">`open(method,url)`</a>*)
* `url` (String) (*<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#open()">`open(method,url)`</a>*)
* `body` (String) (*<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#send()">`send(body)`</a>*)
* `headers` (Object) (*Contains Name-Value pairs set with <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#setRequestHeader()">`setRequestHeader(name,value)`</a>*)
* `timeout` (Number) *([`timeout`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#timeout))*
* `type` (String) *([`responseType`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#responseType))*
* `withCredentials` (String) *([`withCredentials`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#withCredentials))*

### `response` Objesi

* `status` (Number) **Required when for fake `response`s** *([`status`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#status))*
* `statusText` (String) *([`statusText`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#statusText))*
* `text` (String) *([`responseText`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#responseText))*
* `headers` (Object) (*Contains Name-Value pairs retrieved with <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#getAllResponseHeaders()">`getAllResponseHeaders()`</a>*)
* `xml` (XML) *([`responseXML`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#responseXML))*
* `data` (Varies) *([`response`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#response))*

### Referanslar

https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest

http://www.w3.org/TR/XMLHttpRequest/

http://www.w3.org/TR/XMLHttpRequest2/

## EN:
#### MEVLANA is XHR/AJAX interceptor. It modifies requests and responses.

### Features

* Intercept, modify and abort XHR/AJAX request and response
* Compatible with addEventListener and removeEventListener

### Example

In this example, we abort request if url contains "pqo.php":

``` javascript
MEVLANA.before(function(request) {
  if(request.url.match(/pqo.php$/)){
    request.abort();
  }
});
```

## Browser Support
Tested in Chrome, Firefox and Safari

## Warning

:warning: Make sure to include MEVLANA first. (Other libraries may store a conflict with MEVLANA on `XMLHttpRequest`)

## API

### `MEVLANA.before(handler(request[, callback])[, index])`

You can modify any XHR request before it is sent.

To make the `handler` is asynchronous, just include the optional `callback` function, which accepts an optional `response` object.

To return a fake response, just use `return` or `callback()` a `response` object.

### `MEVLANA.after(handler(request, response[, callback]) [, index])`

Modifying any property of the `response` object will modify the underlying XHR before it is received.

To make the `handler` is asynchronous, just include the optional `callback` function.

### `MEVLANA.enable()`

Enables MEVLANA and MEVLANA is enabled by default. It modify the native `XMLHttpRequest` class.

### `MEVLANA.disable()`

Disables MEVLANA. Brings back the native `XMLHttpRequest` class.

---

### `request` Object

* `method` (String) (*<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#open()">`open(method,url)`</a>*)
* `url` (String) (*<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#open()">`open(method,url)`</a>*)
* `body` (String) (*<a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#send()">`send(body)`</a>*)
* `headers` (Object) (*Contains Name-Value pairs set with <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#setRequestHeader()">`setRequestHeader(name,value)`</a>*)
* `timeout` (Number) *([`timeout`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#timeout))*
* `type` (String) *([`responseType`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#responseType))*
* `withCredentials` (String) *([`withCredentials`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#withCredentials))*

### `response` Object

* `status` (Number) **Required when for fake `response`s** *([`status`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#status))*
* `statusText` (String) *([`statusText`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#statusText))*
* `text` (String) *([`responseText`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#responseText))*
* `headers` (Object) (*Contains Name-Value pairs retrieved with <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#getAllResponseHeaders()">`getAllResponseHeaders()`</a>*)
* `xml` (XML) *([`responseXML`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#responseXML))*
* `data` (Varies) *([`response`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#response))*

### Reference

https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest

http://www.w3.org/TR/XMLHttpRequest/

http://www.w3.org/TR/XMLHttpRequest2/
