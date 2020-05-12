---
title: openssl command
---

# openssl 명령어 정리

## Key pair
---
``` bash
# openssl genrsa -out {file name} {numbits}

openssl genrsa -out mykey.key 2048
```

<br />

## CSR
---

### csr 생성
 ``` bash
openssl req -new \
-key mykey.key \
-subj "/CN=CommonName/O=Org/OU=Org Unit/ST=State/L=Locality/C=US" \
-addext "subjectAltName = DNS:abc.com, IP:1.1.1.1" \
-out mycsr.csr

# 키쌍 생성과 동시에 csr 생성
openssl req -new \
-keyout mykey.key \
-newkey rsa:2048 \
-subj "/CN=CommonName/O=Org/OU=Org Unit/ST=State/L=Locality/C=US" \
-addext "subjectAltName = DNS:abc.com, IP:1.1.1.1" \
-out mycsr.csr \
-nodes
```
<br />

### csr 확인
``` bash
openssl req -noout -text -in mycsr.csr
```
<br />


## 기타
---

### 변환
``` bash
openssl x509 -inform DER -in careply.cer -outform PEM -out mypem.pem
```