---
description: Cross-Site Scripting
---

# XSS

## Types of XSS

### Stored XSS

_Stored XSS generally occurs when user input is stored on the target server, such as in a database, in a message forum, visitor log, comment field, etc. And then a victim is able to retrieve the stored data from the web application without that data being made safe to render in the browser._

### Reflected XSS

_Reflected XSS occurs when user input is immediately returned by a web application in an error message, search result, or any other response that includes some or all of the input provided by the user as part of the request, without that data being made safe to render in the browser, and without permanently storing the user provided data._

### DOM Based XSS

_DOM Based XSS is a form of XSS where the entire tainted data flow from source to sink takes place in the browser, i.e., the source of the data is in the DOM, the sink is also in the DOM, and the data flow never leaves the browser. For example, the source \(where malicious data is read\) could be the URL of the page \(e.g., document.location.href\), or it could be an element of the HTML, and the sink is a sensitive method call that causes the execution of the malicious data \(e.g., document.write\)._

![](../../.gitbook/assets/image%20%281%29.png)

## References

* [https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/xss](https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/xss)
* [https://developer.mozilla.org/en-US/docs/Web/API/Document\_Object\_Model/Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
* [https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting](https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting)

