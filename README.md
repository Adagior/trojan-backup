# trojan-backup

https://github.com/trojan-gfw/trojan/releases
https://blog.csdn.net/oLiuKong/article/details/52077754


```
tar -Jxf 
nohup ./trojan >/dev/null 2>&1 &



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

```
