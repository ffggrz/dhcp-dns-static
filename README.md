feste IPs und passende Domain für interne Dienste

Domain: *.ffggrz
IPv4: 10.181.0.100 - 199
IPv6: fdb5:78b:64cc::100 - 199 (wie die IPv6-Vergabe funktioniert muss ich erst nachlesen)

Die Dateien werden alle 15 Minuten vom GW abgeholt. Automatisch wird ein PTR-Record generiert.

Zur Syntax:

MAC,Domain,IPv4

Die Dateien werden von dnsmasq mit der Konfigurationszeile "dhcp-hostsfile" eingelesen.
http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html


Läuft im Moment nur auf GW2!

Eigenartigerweise werden die DNS-Anfragen nur aufgelöst wenn der jenige Host ein Lease vom DHCP hat.
Die IP sollte daher auf den Dienst-Server nicht statisch vergeben werden.
