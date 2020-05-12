---
title: keytool command
---

## Keystore
---
### 생성
``` powershell
keytool -genkey -alias myKeypair -keyalg RSA -keysize 2048 -keystore myKeystore.jks -dname "CN=abc.com,O=myO,OU=myOU,L=Seoul,ST=Seoul,C=KR"
```

### 확인
``` powershell
keytool -list -keystore myKeystore.jks
```

<br/>

## CSR
---
### 생성
``` powershell
keytool -certreq -keystore myKeystore.jks -alias myKeypair -file mymy.csr -ext SAN="dns:abc.com,dns:test.com,ip:1.1.1.1"
 ```

### 확인
``` powershell
keytool -printcertreq mymy.csr
```

<br/>

## Certificate
---
### import
``` powershell
keytool -importcert -keystore myKeystore.jks -alias myKeypair -file replyFromCA.cer
```

### CA certificate
``` powershell
keytool -importcert -keystore myKeystore.jks -file cacert.crt -alias cacert
```


<br/>

## Truststore
---
## 생성
``` bash
```



## 확인
``` bash
```




---