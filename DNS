# Project_One_Class_Python
Project_One_Class_Python
#!/usr/bin/python
import dns.resolver
import argparse
from termcolor import colored

myquery = dns.resolver.Resolver()
domain = "megacorpone.com" 
query_type = [ 'SOA', 'NS', 'MX', 'TXT' ]


def func_dnsfoot(_domain):
    print("OK")
    for _type in query_type:
        answers = myquery.query(_domain, _type)

        for _result in answers:
            print(colored('[*] Registro ' + _type + '  ->', 'green'), _result)

def func_main():
    parser = argparse.ArgumentParser(description='DNS Python - Register Enumeration')
    parser.add_argument('--domain', action="store", dest="domain",  default=domain)
    option = parser.parse_args() 
    domaintarget = option.domain
    func_dnsfoot(domaintarget)


if __name__ == '__main__':
    func_main()


 27  dns/dns_002.py 
@@ -0,0 +1,27 @@
#!/usr/bin/python3.6
import dns.resolver
from termcolor import colored

myquery = dns.resolver.Resolver()
domain = "megacorpone.com" 
lista = [ 'www','www1', 'www2', 'www3', 'admin', 'route', 'vpn', 'siem', 'fw', 'firewall' ]

def dns_tipoa(_host):
    try:
        _answers = myquery.query(_host, 'A')

        for _hostA in _answers:
            return  _hostA
    except:
        pass

def dns_listquery():
    for _word in lista:
        _host = str(_word + "." + domain)
        dns_result = dns_tipoa(_host)

        if dns_result is not None:
            print(colored('[*]', 'green'),_word, "--> ", _host, dns_result)


dns_listquery()
 27  dns/dns_003.py 
@@ -0,0 +1,27 @@
#!/usr/bin/python3.6
import dns.resolver
from termcolor import colored

myquery = dns.resolver.Resolver()
domain = "uol.com.br" 
lista = [ 'www','www1', 'www2', 'www3', 'admin', 'route', 'vpn', 'siem', 'fw', 'firewall' ]

def dns_tipoa(_host):
    try:
        _answers = myquery.query(_host, 'AAAA')

        for _hostA in _answers:
            return  _hostA
    except:
        pass

def dns_listquery():
    for _word in lista:
        _host = str(_word + "." + domain)
        dns_result = dns_tipoa(_host)

        if dns_result is not None:
            print(colored('[*]', 'cyan'),_word, "--> ", _host, dns_result)


dns_listquery()
 50  dns/dns_004.py 
@@ -0,0 +1,50 @@
#!/usr/bin/python3.6

import dns.resolver
from termcolor import colored
from threading import *

msgattack = " Iniciando o FOOTPRINT - DNS Bruteforce" 
myquery = dns.resolver.Resolver()
domain = "megacorpone.com" 

def dns_tipoa(_host):
    try:
        _answers = myquery.query(_host, 'A')

        for _hostA in _answers:
            return  _hostA
    except:
        pass

def dns_listquery(_word):
    _host = str(_word + "." + domain)
    dns_result = dns_tipoa(_host)

    if dns_result is not None:
        print(colored('[*]', "green"),_word, "--> ", _host, dns_result)


def bruteforce_dns_ipv4(_wordlist,_target):
    with open(_wordlist, 'r') as machines:
        while True:
            machine = machines.readline().strip("\n")

            if not machine:
                break 

            try:
                dns_listquery(machine)

            except: 
                pass




### IPv4 enumeration
fastway = Thread(target=bruteforce_dns_ipv4,args=("word2.txt",domain))
print( colored('[*]','blue'), msgattack)
fastway.start()

### IPv6 enumeration
 101  dns/dns_005.py 
@@ -0,0 +1,101 @@
#!/usr/bin/python

import dns.resolver
from termcolor import colored
from threading import *

msgattackipv4 = " Iniciando o FOOTPRINT - DNS Bruteforce - IPv4" 
msgattackipv6 = " Iniciando o FOOTPRINT - DNS Bruteforce - IPv6" 
myquery = dns.resolver.Resolver()
domain = "uol.com.br" 

### IPv4
def dns_tipoa(_host):
    try:
        _answers = myquery.query(_host, 'A')

        for _hostA in _answers:
            return  _hostA
    except:
        pass

def dns_listquery_ipv4(_word):
    _host = str(_word + "." + domain)
    dns_result = dns_tipoa(_host)

    if dns_result is not None:
        print(colored('[*]', "green"),_word, "--> ", _host, dns_result)



def bruteforce_dns_ipv4(_wordlist,_target):
    with open(_wordlist, 'r') as machines:
        while True:
            machine = machines.readline().strip("\n")

            if not machine:
                break 

            try:
                dns_listquery_ipv4(machine)

            except: 
                pass

### IPv6


def dns_tipoipv6(_host):
    try:
        _answers = myquery.query(_host, 'AAAA')

        for _hostA in _answers:
            return  _hostA
    except:
        pass

def dns_listquery_ipv6():
    for _word in lista:
        _host = str(_word + "." + domain)
        dns_result = dns_tipoipv6(_host)

        if dns_result is not None:
            print(colored('[*]', 'cyan'),_word, "--> ", _host, dns_result)


def bruteforce_dns_ipv6(_wordlist,_target):
    with open(_wordlist, 'r') as machines:
        while True:
            machine = machines.readline().strip("\n")

            if not machine:
                break 

            try:
                dns_listquery_ipv6(machine)

            except: 
                pass



### IPv4 enumeration
def func_ipv4_enum():
    fastway = Thread(target=bruteforce_dns_ipv4,args=("wordlist.txt",domain))
    print( colored('[*]','blue'), msgattackipv4)
    fastway.start()

### IPv6 enumeration
def func_ipv6_enum():
    fastway = Thread(target=bruteforce_dns_ipv6,args=("wordlist.txt",domain))
    print( colored('[*]','blue'), msgattackipv6)
    fastway.start()


def func_attack():
    func_ipv4_enum()
    func_ipv6_enum()

func_attack()


 114,606  dns/wordbig.txt 
Large diffs are not rendered by default.

 25  dns/wordlist.txt 
@@ -0,0 +1,25 @@
www
mail
ftp
localhost
webmail
smtp
webdisk
pop
cpanel
whm
ns1
ns2
autodiscover
autoconfig
ns
test
m
blog
dev
www2
ns3
pop3
forum
admin
mail2
 15  param.py 
@@ -0,0 +1,15 @@
import argparse
msg_arg='DNS Python - Register Enumeration'

def func_main():
    parser = argparse.ArgumentParser(description=msg_arg)
    parser.add_argument('--domain', action="store", dest="domain",  default=domain)
    option = parser.parse_args() 
    domaintarget = option.domain
    func_dnsfoot(domaintarget)


if __name__ == '__main__':
    func_main()


 76  setup/requirements.txt 
@@ -0,0 +1,76 @@

aiohttp
ajpy
alive_bar
argparse
asn1crypto
async-timeout
attrs
backdoor-factory
bcrypt
beautifulsoup4
bs4
colorama
datetime
dnspython
dnspython3
figlet
flask
future
geoip2
hashID
hashlib
hpack
httplib2
ipaddress
ipython
ipython-genutils
ldap3
matplotlib
mitmproxy
mss
multidict
multiprocessing
mysqlclient
netaddress
netmiko
numpy
paramiko
passlib
pefile
pexpect
pgdb
Pillow
pip
ply
progressbar2
prompt-toolkit
pyfiglet
Pygments
PyGObject
pyinstaller
pynput
pyperclip
pysmi
pysnmp
PySocks
python3-nmap
python-telegram-bot
pythonwhois
pywhois
pyxdg
requests
scapy
scp
shodan
sleep
socks
sys
termcolor
time
tqdm
urllib3
urlopen
urwid
whois
XlsxWriter
