# Enumeration

* Find SUID binaries
  * `find / -perm -u=s -type f 2>/dev/null`
* Find SGID binaries
  * `find / -perm -g=s -type f 2>/dev/null`
* Find sticky bit binaries
  * `find / -perm -1000 -type d 2>/dev/null`
