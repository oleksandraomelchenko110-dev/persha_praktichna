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
**HTML вивід:**
```
PS C:\Users\my comp> curl.exe -v -L  x.org
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
< Date: Sat, 19 Sep 2026 19:34:42 GMT
< Via: 1.1 varnish
< X-Served-By: cache-fra-eddf8230030-FRA
< X-Cache: HIT
< X-Cache-Hits: 0
< X-Timer: S1789846483.762920,VS0,VE0
< Strict-Transport-Security: max-age=300
<
* shutting down connection #0
* Clear auth, redirects to port from 80 to 443
* Issue another request to this URL: 'https://x.org/'
* Host x.org:443 was resolved.
* IPv6: (none)
* IPv4: 151.101.3.52
*   Trying 151.101.3.52:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Connected to x.org (151.101.3.52) port 443
* using HTTP/1.x
> GET / HTTP/1.1
> Host: x.org
> User-Agent: curl/8.13.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 308 Permanent Redirect
< Connection: keep-alive
< Content-Length: 53
< Content-Type: text/html; charset=utf-8
< Location: http://www.x.org/
< X-Request-Id: e50f9d1ff896f48dee3f8cd7dc540ba0
< Accept-Ranges: bytes
< Date: Sat, 19 Sep 2026 19:34:43 GMT
< Via: 1.1 varnish
< X-Served-By: cache-fra-eddf8230196-FRA
< X-Cache: MISS
< X-Cache-Hits: 0
< Vary: Origin
< Strict-Transport-Security: max-age=300
* Ignoring the response-body
* setting size while ignoring
<
* Connection #1 to host x.org left intact
* Clear auth, redirects to port from 443 to 80
* Issue another request to this URL: 'http://www.x.org/'
* Host www.x.org:80 was resolved.
* IPv6: (none)
* IPv4: 146.75.119.52
*   Trying 146.75.119.52:80...
* Connected to www.x.org (146.75.119.52) port 80
* using HTTP/1.x
> GET / HTTP/1.1
> Host: www.x.org
> User-Agent: curl/8.13.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< Connection: close
< Content-Length: 0
< Server: Varnish
< Retry-After: 0
< Location: https://www.x.org/
< Accept-Ranges: bytes
< Date: Sat, 19 Sep 2026 19:34:44 GMT
< Via: 1.1 varnish
< X-Served-By: cache-fra-eddf8230065-FRA
< X-Cache: HIT
< X-Cache-Hits: 0
< X-Timer: S1789846484.452094,VS0,VE0
< Strict-Transport-Security: max-age=300
<
* shutting down connection #2
* Clear auth, redirects to port from 80 to 443
* Issue another request to this URL: 'https://www.x.org/'
* Host www.x.org:443 was resolved.
* IPv6: (none)
* IPv4: 146.75.119.52
*   Trying 146.75.119.52:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Connected to www.x.org (146.75.119.52) port 443
* using HTTP/1.x
> GET / HTTP/1.1
> Host: www.x.org
> User-Agent: curl/8.13.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Connection: keep-alive
< Content-Length: 9379
< Content-Type: text/html; charset=utf-8
< Cache-Control: max-age=600
< Etag: "848176693e0b283901ae3d32bfa5c3a805658d92dfcfa3fbc3798f642a1cea02"
< Expires: Sat, 19 Sep 2026 19:44:44 UTC
< Last-Modified: Thu, 10 Sep 2026 16:40:18 GMT
< X-Request-Id: cb2b0bad784fa5d60206c7fb9c24cfc3
< Accept-Ranges: bytes
< Age: 0
< Date: Sat, 19 Sep 2026 19:34:44 GMT
< Via: 1.1 varnish
< X-Served-By: cache-fra-eddf8230197-FRA
< X-Cache: MISS
< X-Cache-Hits: 0
< Vary: Accept-Encoding, Origin
< Strict-Transport-Security: max-age=300
<
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="style.css" type="text/css">
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta content="#3b80ae" name="theme-color">
    <meta property="og:site_name" content="xorg">
    <meta property="og:type" content="website">
    <meta property="og:image" content="/icon.png">
    <meta property="twitter:image" content="/icon.png">
    <link rel="icon" href="/icon.png" sizes="16x16" type="image/png">
    <link rel="alternate" type="application/x-wiki" title="Edit this page" href="https://gitlab.freedesktop.org/xorg/wiki/-/edit/main/content/index.mdwn">
    <title>xorg</title>
    <meta property="og:title" content="xorg">
    <meta property="twitter:title" content="xorg">





  </head>
  <body>
    <!-- Works around Firefox bug https://bugzilla.mozilla.org/show_bug.cgi?id=1404468 -->
    <script>0</script>
    <nav>
      <a href="#main" class="main-content" tabindex="0">Skip to Main Content</a>
      <div class="nav-grid">
        <div>
          <a aria-label="Homepage" href="">
            <img alt="" class="logo">
          </a>
        </div>

        <div class="nav-column-align-center nav-column-align-right">


<form method="get" action="https://www.google.com/search" id="searchform">
 <div>
  <input name="sitesearch" value="http://www.x.org/wiki/" type="hidden" />
  <input name="q" value="" id="searchbox" size="16" maxlength="255" type="text"
    placeholder="search" />
 </div>
</form>


        </div>

        <div class="nav-column-align-center backlinks-row">

          <b>X.Org</b>

        </div>

        <div class="nav-column-align-right backlinks-row">
          <a class="nav-link-button" href="https://gitlab.freedesktop.org/xorg/wiki/-/edit/main/content/index.mdwn">Edit</a>



            <a class="nav-link-button" href="https://gitlab.freedesktop.org/xorg/wiki/-/commits/main/content/index.mdwn">Page History</a>



            <a class="nav-link-button" href="https://gitlab.freedesktop.org/xorg/wiki/-/blob/main/content/index.mdwn">Source</a>

        </div>
      </div>
    </nav>

    <main id="main">
      <p>The X.Org project provides an open source implementation of the X Window System. The development work is being done in conjunction with the <a href="http://freedesktop.org">freedesktop.org</a> community.  The <a href="./XorgFoundation/">X.Org Foundation</a> is the educational non-profit corporation whose <a href="./BoardOfDirectors/">Board</a> serves this effort, and whose <a href="./Membership/">Members</a> lead this work. </p>

<p>The last full release of the entire X.Org stack was <a href="./Releases/7.7/">X11R7.7</a> - since then individual X.Org modules have been released independently as needed - see <a href="http://lists.x.org/archives/xorg-announce/">the xorg-announce archives</a> for details of those releases, and <a href="https://www.x.org/releases/individual/">https://www.x.org/releases/individual/</a> for downloads. Information about all <a href="./Releases/">releases</a> is available.  <em>(Important: If you have an older release, please see the <a href="./Development/Security/">Security page</a> for information on security updates.)</em></p>

<div style="float: right; background-color:rgba(255, 255, 0, 0.1); border-radius: 6px; padding: 6px 12px; line-height: 120%" align="center" itemscope itemtype="http://schema.org/Organization">
<link itemprop="url" href="http://www.x.org/">
<link itemtype="logo" itemprop="logo" href="http://www.x.org/wiki/logo.png" />
<div style="padding-bottom: 5px;"><i>Follow <span itemprop="name">X.Org</span> on:</i></div>
<a href="https://floss.social/@XOrgFoundation" rel="me" itemprop="sameAs"><img src="mastodon.png" style="border:0;width:34px;height:34px;" alt="Mastodon" title="Mastodon"/></a>
<a href="https://www.youtube.com/c/XOrgFoundation" rel="publisher" itemprop="sameAs"><img src="youtube.png" style="border:0;width:34px;height:34px;" alt="YouTube" title="YouTube"/></a>
</div>

<p>You may be interested in: </p>

<!--
* <a href="./BoardOfDirectors/Elections/2016/">The 2016 Election to the X.Org Foundation BoD & Vote on Bylaw Changes</a>
* <a href="./BoardOfDirectors/Elections/2015Results/">Results of the 2015 Election to the X.Org Foundation BoD & Vote on Bylaw Changes</a> -->

<ul>
<li><a href="./Documentation/">Documentation</a> </li>
<li>Development-related <a href="./News/">news</a>. </li>
<li>X.Org <a href="./Events/">events</a>. </li>
<li><a href="./Other/Press/">Press releases</a>. </li>
<li><a href="./XorgFoundation/Reports/">The Annual Report on the State of the X.Org Foundation</a> </li>
<li><a href="./RelatedProjects/">Related projects</a>. </li>
</ul>

<h2 id="reportingproblemsaskingquestionsandgettinghelp">Reporting problems, asking questions and getting help</h2>

<ul>
<li>Check to see if your question is answered in the <a href="./FAQ/">FAQ</a>.</li>
<li>Check the issues for the <code>xorg</code> group in the <a href="https://gitlab.freedesktop.org/groups/xorg/-/issues">freedesktop gitlab</a> to report bugs against X.Org. </li>
<li>Check the <a href="http://lists.freedesktop.org/archives/xorg/">Xorg mailing list archives</a> </li>
<li>Send other questions or comments to <a href="mailto:xorg@freedesktop.org">the xorg mailing list</a>. </li>
<li>Or get help on <a href="./XorgIRC/">XorgIRC</a>. </li>
</ul>

<h2 id="development">Development</h2>

<ul>
<li>The <a href="./DeveloperStart/">DeveloperStart</a> page includes information for developers along with links to per-module developer pages. </li>
</ul>

<h2 id="mailinglists">Mailing Lists</h2>

<p>On <a href="./XorgMailingLists/">XorgMailingLists</a> you can find a list of X-related mailing lists hosted on lists.freedesktop.org.  More mailing lists on X Window System and related technologies along with subscription directions are available at <a href="http://lists.x.org/">XOrg Foundation</a>.</p>

<h2 id="gettingx">Getting X</h2>

<p>The best place to get X is from your operating system or distribution vendor.  X.Org currently provides no binaries. </p>

<p>There are many <a href="./Mirrors/">Mirrors</a> from which you can download source code to the X Window System. If you would like to be a mirror, feel free to do so and add yourself to the <a href="./Mirrors/">Mirrors</a> page. </p>

<p>Development snapshots are currently on hiatus; most modules now update slowly enough that frequent snapshots aren't needed. </p>

<h2 id="security">Security</h2>

<p>For security advisories please check our <a href="./SecurityPage/">SecurityPage</a>. </p>

<p>Please notify us of any security issues by sending mail to <a href="mailto:xorg_security@x.org">xorg_security@x.org</a> . </p>

<h2 id="sponsorshipanddonations">Sponsorship and Donations</h2>

<p>The X.Org Foundation welcomes sponsorship (both cash and in-kind), and tries hard to put the donations of sponsors to transparent good use.  The Foundation is an extremely low-overhead all-volunteer organization.  If you are interested in contributing, please see our <a href="./SponsorshipPage/">SponsorshipPage</a>. </p>

<p><strong>Donate via SFC's PayPal:</strong></p>

<form action="https://www.paypal.com/donate" method="post" target="_top">
<input type="hidden" name="hosted_button_id" value="67Y5PU5CG5V2A" />
<input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif" border="0" name="submit" title="PayPal - The safer, easier way to pay online!" alt="Donate with PayPal button" />
<img alt="" border="0" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
</form>

<p><strong>Donation via check or money order:</strong></p>

<p>Make your check payable to Software Freedom Conservancy and write "X.org" in the
memo or reference field. For more information including the mailing address,
and details on possible wire transfer please see
<a href="https://sfconservancy.org/donate/">https://sfconservancy.org/donate/</a></p>

<h2 id="acknowledgements">Acknowledgements</h2>

<p>Our thanks go to <a href="http://www.pdx.edu/">Portland State University</a> for providing the hosting of x.org/freedesktop.org, to <a href="http://hp.com">HP</a> for providing the x.org/freedesktop.org hardware, and others who have provided generous financial sponsorship and in-kind support.</p>

<p>Our thanks also go to the contributors to the X Window System technology over the years. Many of these are acknowledged in previous distribution <a href="http://www.x.org/X11R6.8.0/doc/RELNOTES6.html">release notes</a>. </p>

<h2 id="copying">Copying</h2>

<p>The content of this wiki is licensed under the <a href="http://opensource.org/licenses/mit-license.php" rel="license">MIT License</a> unless stated otherwise by the author of specific wiki pages.</p>

<p>This license has been selected to ease documentation sharing with the xserver source code.</p>




    </main>

    <footer>
      <div class="footer-text">











        <p><i>Last edited <time datetime="2026-09-10T16:40:10Z">Thu Sep 10 16:40:10 2026</time></i></p>



      </div>
    </footer>
  </body>
</html>
* Connection #3 to host www.x.org left intact
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

**Resolve-DnsName x.org (перше виконання):**

**Вивід:** 

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
x.org                                          A      6473  Answer     151.101.3.52
```

**Resolve-DnsName x.org (повторне виконання через 5–7 хвилин):**

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

> 130

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

>
* Host x.org:80 was resolved.
* IPv6: (none)
* IPv4: 151.101.3.52
* Trying 151.101.3.52:80...
* Connected to x.org (151.101.3.52) port 80
* using HTTP/1.x

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

> 443 - порт для https за замовчунянням. Тому він автоматично підставляється. 

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

>  Він зменшився з 6473 до 6079, це показує, скільки залишилося пакету до знищється.

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` | Прострочений термін дії сертифікату |
| `wrong.host` | Сертифікат призначен для іншої адреси  |
| `self-signed` | Сертифікат не підтвердженний третьою стороною. |

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | * ALPN: curl offers http/1.1 | А.1 |
| 2 | < Accept-Ranges: bytes | А.1 |
| 3 | * schannel: disabled automatic use of client certificate | А.1 |

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
