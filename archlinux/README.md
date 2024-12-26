# Arch Linux Kerberos authentication

Kerberos service 


```bash
cat >> /etc/hosts <<EOL
172.19.0.2 kdc.jai.net
172.19.0.3 kclient.jai.net
172.19.0.4 kssh.jai.net
EOL
```


References:  
[Kerberos Arch Wiki](https://wiki.archlinux.org/title/Kerberos)  
[Kerberos OpenSsh Wiki](https://wiki.archlinux.org/title/OpenSSH)  