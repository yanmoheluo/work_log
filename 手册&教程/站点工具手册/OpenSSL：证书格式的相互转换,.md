OpenSSL转换PEM
将PEM转换为DER

openssl x509 -outform der -in certificate.pem -out certificate.der

将PEM转换为P7B

openssl crl2pkcs7 -nocrl -certfile certificate.cer -out certificate.p7b -certfile CACert.cer

将PEM转换为PFX

openssl pkcs12 -export -out certificate.pfx -inkey privateKey.key -in certificate.crt -certfile CACert.crt

OpenSSL转换DER
将DER转换为PEM

openssl x509 -inform der -in certificate.cer -out certificate.pem

OpenSSL转换P7B
将P7B转换为PEM

openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer

将P7B转换为PFX

openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer

openssl pkcs12 -export -in certificate.cer -inkey privateKey.key -out certificate.pfx -certfile CACert.cer

OpenSSL转换PFX
将PFX转换为PEM

openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes

如果需要将Java Keystore文件转换为其他格式，通常可以更轻松地创建新的私钥和证书，但可以将Java Keystore转换为PEM格式。