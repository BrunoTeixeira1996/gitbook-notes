---
description: Enum is everything
---

# Enumeration

## cURL

Some useful cURL commands to interact with a web app 

```bash
curl -X OPTIONS target.com  # Find all supported options for "target.com"
curl -s --head target.com | grep -i server  # Find out what server info is provided by the server
curl -d "param1=value&param2=value" https://target.com/something.php  # Send parameters with curl
```

## Web app components

Its really important to understand what components \(web server, cms, database, etc\) a web app is using.

* **Wappalyzer** -&gt; [https://www.wappalyzer.com/?gclid=CjwKCAjw95yJBhAgEiwAmRrutK6zgZlDEEVJEiGHxHgqoaxOKXNubEwJAu9Y7FfZEeGAlq9Q8N6OChoCrYIQAvD\_BwE](https://www.wappalyzer.com/?gclid=CjwKCAjw95yJBhAgEiwAmRrutK6zgZlDEEVJEiGHxHgqoaxOKXNubEwJAu9Y7FfZEeGAlq9Q8N6OChoCrYIQAvD_BwE)
* **Shodan** -&gt; [https://www.shodan.io/](https://www.shodan.io/)
* **whatweb** -&gt; [https://tools.kali.org/web-applications/whatweb](https://tools.kali.org/web-applications/whatweb)

## Fuzzing

_Wfuzz provides a framework to automate web applications security assessments and could help you to secure your web applications by finding and exploiting web application vulnerabilities._

* **Below is shown an example of wfuzz looking for common directories**

```bash
wfuzz -w wordlist/general/common.txt http://testphp.vulnweb.com/FUZZ 
```

* **Below is shown an example of wfuzz looking for common files**

```bash
wfuzz -w wordlist/general/common.txt http://testphp.vulnweb.com/FUZZ.php
```

* [https://owasp.org/www-community/Fuzzing](https://owasp.org/www-community/Fuzzing)
* [https://github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)
* [https://wfuzz.readthedocs.io/en/latest/user/basicusage.html](https://wfuzz.readthedocs.io/en/latest/user/basicusage.html)



## Tools

### [Gobuster](https://github.com/OJ/gobuster)

* **Directory list**

```bash
gobuster dir -u http://target.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

* **Virtual Host Enumeration**

```bash
gobuster vhost -u https://target.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

### [Droopescan](https://github.com/droope/droopescan)

* **Simple scan with 32 threads**

```bash
droopescan scan drupal -u http://example.org/ -t 32
```

### [Moodlescan](https://github.com/inc0d3/moodlescan)

* **Simple scan to find moodle vulns**

```bash
python moodlescan.py -u http://example.org/
```

### [WPScan](https://github.com/wpscanteam/wpscan)

* **Simple scan using the default options**

```bash
wpscan --url example.org
```

