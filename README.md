# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім'я** | *Омельченко Олександра* |
| **Група** | *ІПЗ 2.01* |
| **Номер варіанта** | *23* |
| **Домен варіанта** | *x.org* |
| **Середовище виконання** | *Windows* |
| **Версія curl** | *curl 8.13.0 (Windows) libcurl/8.13.0 Schannel zlib/1.3.1 WinIDN* |
| **Дата виконання** | *19.09.2026* |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```
curl -v https://ВАШ_ДОМЕН
```

**Вивід:**

```
PS C:\Users\my comp> curl.exe -v x.org
* Host x.org:80 was resolved.
* IPv6: (none)
* IPv4: 151.101.3.52
*   Trying 151.101.3.52:80...
* Connected to x.org (151.101.3.52) port 80
* using HTTP/1.x
> GET / HTTP/1.1
> Host: x.org
> User-Agent: curl/8.13.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< Connection: close
< Content-Length: 0
< Server: Varnish
< Retry-After: 0
< Location: https://x.org/
< Accept-Ranges: bytes
< Date: Sat, 19 Sep 2026 19:09:31 GMT
< Via: 1.1 varnish
< X-Served-By: cache-fra-eddf8230105-FRA
< X-Cache: HIT
< X-Cache-Hits: 0
< X-Timer: S1789844971.233058,VS0,VE0
< Strict-Transport-Security: max-age=300
<
* shutting down connection #0
```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl -v http://neverssl.com
```

**Вивід:**

```
PS C:\Users\my comp> curl -v http://neverssl.com
ПОДРОБНО: GET http://neverssl.com/ with 0-byte payload
ПОДРОБНО: received 3961-byte response of content type text/html; charset=UTF-8


StatusCode        : 200
StatusDescription : OK
Content           : <html>
                        <head>
                                <title>NeverSSL - Connecting ... </title>
                                <style>
                                body {
                                        font-family: Montserrat, helvetica, arial, sans-serif;
                                        font-size: 16x;
                                        color: #444444;
                                        margin: 0;
                                }
                                h2 {
                        ...
RawContent        : HTTP/1.1 200 OK
                    Upgrade: h2,h2c
                    Connection: Upgrade, Keep-Alive
                    Vary: Accept-Encoding
                    Keep-Alive: timeout=5, max=100
                    Accept-Ranges: bytes
                    Content-Length: 3961
                    Content-Type: text/html; charset=U...
Forms             : {}
Headers           : {[Upgrade, h2,h2c], [Connection, Upgrade, Keep-Alive], [Vary, Accept-Encoding], [Keep-Alive,
                    timeout=5, max=100]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 3961
```

---

### A.3. Запит до служби доменних імен

`Resolve-DnsName x.org`

```
**Команда (перше виконання):**
```
**Вивід:** 

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
x.org                                          A      6473  Answer     151.101.3.52
```

**Команда (повторне виконання через 5–7 хвилин):**

**Вивід:**

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
x.org                                          A      6079  Answer     151.101.3.52
```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) | 22:13 | 22:20 |
| IP-адреса | 151.101.3.52 | 151.101.3.52 |
| Значення TTL | 6473 | 6079 |

> Якщо друге значення TTL виявилося більшим за перше — це нормально: кеш резолвера встиг оновитися. Зафіксуйте як є.

---

### A.4. Контрольний ресурс

**Команда:**

```
curl -v https://google.com
```

**Вивід:**

```
PS C:\Users\my comp> curl -v https://google.com
ПОДРОБНО: GET https://google.com/ with 0-byte payload
ПОДРОБНО: received -1-byte response of content type text/html; charset=UTF-8


StatusCode        : 200
StatusDescription : OK
Content           : <!doctype html><html itemscope="" itemtype="http://schema.org/WebPage" lang="uk"><head><meta
                    content="text/html; charset=UTF-8" http-equiv="Content-Type"><meta
                    content="/images/branding/googleg/1x/goo...
RawContent        : HTTP/1.1 200 OK
                    Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src
                    'nonce-4F9YkujpDuWVIGHn_arHzQ' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline'
                    https: ...
Forms             : {f}
Headers           : {[Content-Security-Policy-Report-Only, object-src 'none';base-uri 'self';script-src
                    'nonce-4F9YkujpDuWVIGHn_arHzQ' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline'
                    https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp], [Accept-CH,
                    Sec-CH-Prefers-Color-Scheme], [X-XSS-Protection, 0], [X-Frame-Options, SAMEORIGIN]...}
Images            : {@{innerHTML=; innerText=; outerHTML=<IMG style="BORDER-TOP-STYLE: none; BORDER-LEFT-STYLE: none;
                    BORDER-BOTTOM-STYLE: none; BORDER-RIGHT-STYLE: none; DISPLAY: none" alt=""
                    src="https://ssl.gstatic.com/gb/images/bar/al-icon.png" width=24 height=24>; outerText=;
                    tagName=IMG; style=BORDER-TOP-STYLE: none; BORDER-LEFT-STYLE: none; BORDER-BOTTOM-STYLE: none;
                    BORDER-RIGHT-STYLE: none; DISPLAY: none; alt=;
                    src=https://ssl.gstatic.com/gb/images/bar/al-icon.png; width=24; height=24}, @{innerHTML=;
                    innerText=; outerHTML=<IMG id=hplogo style="PADDING-BOTTOM: 14px; PADDING-TOP: 28px; PADDING-LEFT:
                    0px; PADDING-RIGHT: 0px" alt=Google
                    src="/images/branding/google_wordmark/v1/1x/googlelogo_color_white_background_272x92dp.png"
                    width=272 height=92>; outerText=; tagName=IMG; id=hplogo; style=PADDING-BOTTOM: 14px; PADDING-TOP:
                    28px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; alt=Google;
                    src=/images/branding/google_wordmark/v1/1x/googlelogo_color_white_background_272x92dp.png;
                    width=272; height=92}, @{innerHTML=; innerText=; outerHTML=<IMG id=tsuid_q-Cuarf2BdnNwPAPi7q7kQ8_1
                    style="CURSOR: pointer; RIGHT: 5px; POSITION: absolute; Z-INDEX: 300; TOP: 4px" alt=""
                    src="/textinputassistant/tia.png" width=27 height=23
                    data-script-url="/textinputassistant/13/uk_tia.js">; outerText=; tagName=IMG;
                    id=tsuid_q-Cuarf2BdnNwPAPi7q7kQ8_1; style=CURSOR: pointer; RIGHT: 5px; POSITION: absolute;
                    Z-INDEX: 300; TOP: 4px; alt=; src=/textinputassistant/tia.png; width=27; height=23;
                    data-script-url=/textinputassistant/13/uk_tia.js}}
InputFields       : {@{innerHTML=; innerText=; outerHTML=<INPUT type=hidden value=uk name=hl>; outerText=;
                    tagName=INPUT; type=hidden; value=uk; name=hl}, @{innerHTML=; innerText=; outerHTML=<INPUT
                    type=hidden value=hp name=source>; outerText=; tagName=INPUT; type=hidden; value=hp; name=source},
                    @{innerHTML=; innerText=; outerHTML=<INPUT type=hidden name=biw>; outerText=; tagName=INPUT;
                    type=hidden; name=biw}, @{innerHTML=; innerText=; outerHTML=<INPUT type=hidden name=bih>;
                    outerText=; tagName=INPUT; type=hidden; name=bih}...}
Links             : {@{innerHTML=Gmail; innerText=Gmail; outerHTML=<A aria-label="Gmail " class=gb_6
                    href="https://mail.google.com/mail/&amp;ogbl" target=_top data-pid="23">Gmail</A>;
                    outerText=Gmail; tagName=A; aria-label=Gmail ; class=gb_6;
                    href=https://mail.google.com/mail/&amp;ogbl; target=_top; data-pid=23}, @{innerHTML=Зображення;
                    innerText=Зображення; outerHTML=<A aria-label="Пошук зображень " class=gb_6
                    href="https://www.google.com/imghp?hl=uk&amp;ogbl" target=_top data-pid="2">Зображення</A>;
                    outerText=Зображення; tagName=A; aria-label=Пошук зображень ; class=gb_6;
                    href=https://www.google.com/imghp?hl=uk&amp;ogbl; target=_top; data-pid=2}, @{innerHTML=<SVG
                    aria-hidden=true class=gb_H viewbox="0 0 24 24" focusable="false"><PATH d="M6,8c1.1,0 2,-0.9
                    2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2zM12,20c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2
                    2,2zM6,20c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2zM6,14c1.1,0 2,-0.9 2,-2s-0.9,-2
                    -2,-2 -2,0.9 -2,2 0.9,2 2,2zM12,14c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2
                    2,2zM16,6c0,1.1 0.9,2 2,2s2,-0.9 2,-2 -0.9,-2 -2,-2 -2,0.9 -2,2zM12,8c1.1,0 2,-0.9 2,-2s-0.9,-2
                    -2,-2 -2,0.9 -2,2 0.9,2 2,2zM18,14c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2
                    2,2zM18,20c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2z"></PATH><IMG
                    style="BORDER-TOP-STYLE: none; BORDER-LEFT-STYLE: none; BORDER-BOTTOM-STYLE: none;
                    BORDER-RIGHT-STYLE: none; DISPLAY: none" alt=""
                    src="https://ssl.gstatic.com/gb/images/bar/al-icon.png" width=24 height=24></IMG></SVG>;
                    innerText=; outerHTML=<A aria-expanded=false role=button tabIndex=0 aria-label="Додатки Google"
                    class=gb_C href="https://www.google.com.ua/intl/uk/about/products"><SVG aria-hidden=true
                    class=gb_H viewbox="0 0 24 24" focusable="false"><PATH d="M6,8c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2
                    -2,0.9 -2,2 0.9,2 2,2zM12,20c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2zM6,20c1.1,0
                    2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2zM6,14c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2
                    0.9,2 2,2zM12,14c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2zM16,6c0,1.1 0.9,2
                    2,2s2,-0.9 2,-2 -0.9,-2 -2,-2 -2,0.9 -2,2zM12,8c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2
                    2,2zM18,14c1.1,0 2,-0.9 2,-2s-0.9,-2 -2,-2 -2,0.9 -2,2 0.9,2 2,2zM18,20c1.1,0 2,-0.9 2,-2s-0.9,-2
                    -2,-2 -2,0.9 -2,2 0.9,2 2,2z"></PATH><IMG style="BORDER-TOP-STYLE: none; BORDER-LEFT-STYLE: none;
                    BORDER-BOTTOM-STYLE: none; BORDER-RIGHT-STYLE: none; DISPLAY: none" alt=""
                    src="https://ssl.gstatic.com/gb/images/bar/al-icon.png" width=24 height=24></IMG></SVG></A>;
                    outerText=; tagName=A; aria-expanded=false; role=button; tabIndex=0; aria-label=Додатки Google;
                    class=gb_C; href=https://www.google.com.ua/intl/uk/about/products}, @{innerHTML=<SPAN
                    class=gb_le>Увійти</SPAN>; innerText=Увійти; outerHTML=<A aria-label=Увійти class="gb_4a gb_6d
                    gb_Xd gb_Od" href="https://accounts.google.com/ServiceLogin?hl=uk&amp;passive=true&amp;continue=htt
                    ps://www.google.com/&amp;ec=GAZAmgQ" target=_top><SPAN class=gb_le>Увійти</SPAN></A>;
                    outerText=Увійти; tagName=A; aria-label=Увійти; class=gb_4a gb_6d gb_Xd gb_Od; href=https://account
                    s.google.com/ServiceLogin?hl=uk&amp;passive=true&amp;continue=https://www.google.com/&amp;ec=GAZAmg
                    Q; target=_top}...}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 88875
```

---
### A.5. Ресурси з некоректною конфігурацією сертифіката

**Випадок 1**


```
curl -v https://expired.badssl.com
```

```
PS C:\Users\my comp> curl.exe -v https://expired.badssl.com
* Host expired.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - Получен сертификат с истекшим сроком действия.
* closing connection #0
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - Получен сертификат с истекшим сроком действия.
```

**Випадок 2**

```
curl -v https://wrong.host.badssl.com
```

```
PS C:\Users\my comp> curl.exe -v https://wrong.host.badssl.com
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - Главное конечное имя неверно.
* closing connection #0
curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - Главное конечное имя неверно.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

**Випадок 3**

```
curl -v https://self-signed.badssl.com
```

```
PS C:\Users\my comp> curl.exe -v https://self-signed.badssl.com
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - Цепочка сертификатов выпущена центром сертификации, не имеющим доверия.
* closing connection #0
curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - Цепочка сертификатов выпущена центром сертификации, не имеющим доверия.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

> Якщо використано альтернативний спосіб із параметром `--resolve` — зазначити це та навести фактичну команду.

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** ___

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |
| 7 | | | |

*Групи впорядковано від найближчої до користувача (№ 1) до найближчої до апаратного забезпечення. Зайві рядки вилучити, за потреби — додати.*

**Рядки, які не вдалося віднести до жодної групи:**

| Рядок виводу | Причина утруднення |
|---|---|
| | |
| | |
| | |

---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**

> 

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

> 

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

> 

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

> 

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` | |
| `wrong.host` | |
| `self-signed` | |

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

*Пояснення до цих рядків не потрібне.*

---

## Висновки

*150–300 слів. Спиратися на власні спостереження, а не на матеріал лекції.*

**D.1. Що виявилося неочевидним або несподіваним**

*Назвати конкретно, з посиланням на рядок виводу.*

> 

**D.2. Чому саме така кількість груп у частині B**

*На якій підставі ухвалено рішення. Що змусило б його змінити.*

> 

**D.3. Питання, яке залишилося без відповіді**

> 

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано / не використано *(потрібне залишити)*

**Установлений рівень для цієї роботи:** Р3 — ШІ як співвиконавець

**Фактичний рівень використання:** Р___

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
| | | |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---

## Примітки виконавця

*(необов'язковий розділ: що не спрацювало, які команди довелося змінити, які виникли труднощі)*

> 
