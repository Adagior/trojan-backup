# trojan-backup

https://github.com/trojan-gfw/trojan/releases

https://blog.csdn.net/oLiuKong/article/details/52077754

https://gist.github.com/zapstar/4b51d7cfa74c7e709fcdaace19233443

zerossl.com
```
tar -Jxf 
nohup ./trojan >/dev/null 2>&1 &


git clone https://github.com/letsencrypt/letsencrypt
cd letsencrypt
./certbot-auto --help all
./letsencrypt-auto certonly --standalone --email legend_ko@msn.com -d legend-ko.xyz

/etc/letsencrypt/live/legend-ko.xyz/fullchain.pem
/etc/letsencrypt/live/legend-ko.xyz/privkey.pem

yum install openssl -y

openssl genrsa -out server.key 1024
openssl rsa -in server.key -pubout -out server.pem
openssl genrsa -out client.key 1024
openssl rsa -in client.key -pubout -out client.pem

openssl genrsa -out ca.key 1024
openssl req -new -key ca.key -out ca.csr
openssl x509 -req -in ca.csr -signkey ca.key -out ca.crt

openssl req -new -key server.key -out server.csr
openssl x509 -req -CA ca.crt -CAkey ca.key -CAcreateserial -in server.csr -out server.crt

openssl req -new -key client.key -out client.csr
openssl x509 -req -CA ca.crt -CAkey ca.key -CAcreateserial -in client.csr -out client.crt

openssl rsa -in server.key -out server_nopwd.key
openssl x509 -req -days 365 -in server.csr -signkey server_nopwd.key -out server.crt


server.crt
server.key
```





```
[Endpoint]
Socks-Out, builtin, socks, address=127.0.0.1, port=1080
Direct, builtin, freedom, domainStrategy=UseIP
Dns-Out, builtin, dns

[RoutingRule]
PROCESS-NAME, trojan.exe, Direct
DOMAIN-KEYWORD, geosite:cn, Direct
GEOIP, cn, Direct
GEOIP, private, Direct
FINAL, Proxy-1

[Dns]
hijack = Dns-Out

[DnsServer]
localhost
8.8.8.8, 53, Remote
8.8.4.4

```
