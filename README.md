# dhcp-dns-static

Hier werden feste IPs und die passende Domain für interne Dienste festgelegt

### Richtlinien

- **Domain:** *.ffggrz
- **IPv4:** 10.181.0.100 - 199
- **IPv6:** fdb5:78b:64cc::100 - 199 (wird erstmal nicht unterstützt)

### Syntax

`[<hwaddr>][,id:<client_id>|*][,set:<tag>][,<ipaddr>][,<hostname>][,<lease_time>][,ignore]`

Wir nutzen davon aber nur drei Optionen:  
MAC, Domain, IPv4


__Beispiel:__  
> `# Kommentar`  
> `00:11:22:AA:BB:CC,beispiel.ffggrz,10.181.0.101`


### Hinweise

Die Dateien werden alle 15 Minuten vom den Gateways synchronisiert.

Die Dateien werden von [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html) mit der Konfigurationszeile "dhcp-hostsfile" eingelesen.
Die PTR-Records werden von einem Script automatisch erzeugt.


__! Läuft im Moment nur auf GW2 !__

Die DNS-Anfragen werden nur aufgelöst wenn derjenige Host ein Lease vom DHCP hat.
Die IP sollte daher auf den Dienst-Server nicht statisch vergeben werden.
