Corporate Pentest 1 writeup *Zonedv6*

___
We were initially given the domain bob.cysca

If we do *host -t mx bob.cysca* we see that it's DNS is managed by ns.bob.cysca and ns6.bob.cysca

Attempting a zone transfer with *nslookup -type=axfr bob.cysca ns6.bob.cysca* contained these two lines in the output
___

flag.udp.bob.cysca    service = 10 10 34532 axfr6flag.bob.cysca.

___
From this we can see axfr6flag.bob.cysca has a service running on port 34532

using openbsd-nc we can connect to it by executing

*nc -6v axfr6flag.bob.cysca* 

and it will print the flag
