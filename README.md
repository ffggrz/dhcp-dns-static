# dhcp-dns-static

Hier werden feste IPs und die passende Domain für interne Dienste festgelegt

### Richtlinien

- **Domain:** *.ffggrz
- **IPv4:** 10.181.0.100 - 199
- **IPv6:** fdb5:78b:64cc::100 - 199 (wird erstmal nicht unterstützt)

### Syntax für ffggrz-static.conf

`dhcp-host=[<hwaddr>][,id:<client_id>|*][,set:<tag>][,<ipaddr>][,<hostname>][,<lease_time>][,ignore]`  

Wir nutzen davon aber nur zwei Optionen:  
MAC, IPv4


__Beispiel:__  
> `# Kommentar (Kontakt / Name)`  
> `dhcp-host=00:11:22:AA:BB:CC,10.181.0.101`  
> `dhcp-host=00:11:22:AA:BB:CC,10.181.0.101`  

### Syntax für ffggrz-dns.conf

`address=/<domain>/[domain/][<ipaddr>]`  
`mx-host=<mx name>[[,<hostname>],<preference>]`  
`cname=<cname>,<target>`  


__Beispiel:__  
> `# Kommentar (Kontakt / Name)`  
> `address=/beispiel.ffggrz/10.181.0.101`  
> `address=/beispiel.ffggrz/beispiel2.ffggrz/10.181.0.101`  
> `mx-host=mx01.beispiel.ffggrz,beispiel.ffggrz`  
> `cname=beispiel.ffggrz,beispiel2.ffggrz`  


### Hinweise

Die Dateien werden alle 15 Minuten von den Gateways synchronisiert.

Die Dateien werden von [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html) mit der Konfigurationszeile "conf-dir" eingelesen.
Einträge aus ffggrz-static erhalten per Script automatisch einen PTR-Record.

