### localca

- create_ca.sh: this script is used to create the local CA. Once you create the CA cert, import the cert to your device and keep the cert and key safe

```
sh create_sa.sh
```

- create_cert.sh: this script is used to generate certificate for your domains in future

```
sh create_cert.sh
```

### Example

```
$ sh create_ca.sh
Enter Output CA Filename without Extension: mac-home-ca
Enter CA Name (eg. My Home):mac-home-ca


 (+) Generating CA KeyGenerating RSA private key, 2048 bit long modulus
...............................................+++
.............................+++
e is 65537 (0x10001)
Enter pass phrase for mac-home-ca.key:
Verifying - Enter pass phrase for mac-home-ca.key:


 (+) Generating Root CertificateEnter pass phrase for mac-home-ca.key:
```

```
$ sh create_cert.sh
Enter Common Name (Site Name, eg. something.test.home): test.local.home
Enter CA FileName: mac-home-ca
Generating RSA private key, 2048 bit long modulus
..........................................................................................................+++
..............................................................................................+++
e is 65537 (0x10001)
Signature ok
subject=/C=US/ST=California/L=San Francisco/CN=test.local.home
Getting CA Private Key
Enter pass phrase for mac-home-ca.key:
```

```
# Modify local DNS
$ sudo vim /etc/hosts
127.0.0.1 test.local.home
```

Install CA on Mac

- Open CA pem file (mac-home-ca.pem) using Keychains
- Click on System -> File -> Import items and select the CA pem file
- Open the certificate and change the trust to "Always trust"
