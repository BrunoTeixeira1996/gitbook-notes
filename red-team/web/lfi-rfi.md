---
description: Local File Inclusion / Remote File Inclusion
---

# LFI/RFI

Local File Inclusion and Remote File Inclusion \(RFI\) are two common vulnerabilities that typically affect PHP web applications. 

**In an LFI vulnerability, the included file is already present on the local application server, targeted by the hacker. If successful, the attacker can read important files, access more sensitive information, or run arbitrary commands.**

**RFI occurs, for example, when a page receives, as input, the path to the file that has to be included and this input is not properly sanitized, allowing the external URL to be injected.**

**Since PHP supports native functions that allow users to include remote files, web applications written in PHP code are more susceptible to RFI attacks.**

The main difference between an LFI and an RFI is the included file’s point of origin. In an LFI attack, threat actors use a local file that is stored on the target server to execute a malicious script. These types of attacks can be carried out by using only a web browser. In an RFI attack, they use a file from an external source.

## LFI

![](../../.gitbook/assets/image%20%283%29.png)

![](../../.gitbook/assets/image%20%284%29.png)

## RFI

![](../../.gitbook/assets/image%20%285%29.png)

## References

* [https://spanning.com/blog/file-inclusion-vulnerabilities-lfi-rfi-web-based-application-security-part-9/](https://spanning.com/blog/file-inclusion-vulnerabilities-lfi-rfi-web-based-application-security-part-9/)
* [https://github.com/payloadbox/rfi-lfi-payload-list](https://github.com/payloadbox/rfi-lfi-payload-list)

