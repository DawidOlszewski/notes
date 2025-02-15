# Certificates x509


### gen rsa key

`openssl genpkey -algorithm RSA -out ca.key -pkeyopt rsa_keygen_bits:4096`

### create CA with it
1. `mkdir -p /CA/prask/{certs,private}`
2. `touch /CA/prask/index.txt`
3. `echo 2025 > /CA/prask/serial`
4. `chmod 0 /CA/prask/{private,index.txt,serial,newcerts}`
5. `chmod -R /CA`
6. create `ca.conf`
```bash
[ ca ]
default_ca = CA_default

[ CA_default ]
dir               = /CA/prask
certs             = $dir/certs
#crl_dir           = $dir/crl
new_certs_dir     = $dir/newcerts
database          = $dir/index.txt
serial            = $dir/serial
#crlnumber         = $dir/crlnumber
#crl               = $dir/crl.pem
certificate       = $dir/ca.cert
private_key       = $dir/private/ca.key
#RANDFILE          = $dir/private/.rand
default_days      = 375
default_md        = sha256        # Default signature algorithm

#default_crl_days  = 30
default_md        = sha256
#preserve          = no
policy    = policy_anything # Default policy

[ policy_anything ]
commonName = supplied

[ req ]
prompt = no
default_bits        = 4096
default_md          = sha256
distinguished_name  = dn_req
x509_extensions     = v3_req

[ dn_ca ]
CN                  = dla-opornych Root
O                   = dla-opornych
C                   = PL


[ dn_req ]
CN = dla-opornych.pl


[ v3_ca ]
basicConstraints    = critical, CA:true, pathlen:0
keyUsage            = critical, keyCertSign, cRLSign
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid:always,issuer

[ v3_req ]
basicConstraints = CA:FALSE
keyUsage = digitalSignature, keyEncipherment
extendedKeyUsage = serverAuth, clientAuth
subjectAltName =    @alt_names

[alt_names]
DNS.1 = dla-opornych.pl


```

7. `openssl req -x509 -key /CA/prask/private/ca.key -days 3650 -out /CA/prask/certs/ca.crt -config /CA/prask/ca.cnf`
   * `-x509` generate certificate not just certification request
### create a Leaf certificate

1. `openssl genpkey -algorithm RSA -out dla-opornych.key -pkeyopt rsa_keygen_bits:4096`
2. `openssl req -new -key dla-opornych.key -out dla-opornych.csr -config /CA/prask/ca.cnf`
3. `openssl ca -in dla-opornych.csr -out dla-opornych.crt -config /CA/prask/ca.cnf`
  




# openssl version -d and /etc/ssl/openssl.cnf

# policy in CA

## openssl

| Subcommand | Purpose	Commo          | Operations                                            |
| ---------- | ---------------------- | ----------------------------------------------------- |
| `req`      | Generate CSRs and keys | Generate CSRs, self-signed certs                      |
| `ca`       | Act as a CA            | Sign CSRs, revoke certs, generate CRLs                |
| `x509`     | Manage certificates    | View certs, convert formats, create self-signed certs |

`DN` - distinguished name. It contains everything below:
* `CN` - common name is a `FQDN` (fully qualified domain name)
* `O` - organization (if personal use put name)
* `OU` - organization unit (if personal use put )
* `C` - country
* `ST` - state



```bash

```

put it in openssl.conf
```bash 
[ CA_default ]
dir               = /etc/ssl/myCA       # The main CA directory
certs             = $dir/certs          # Where issued certs are kept
#new_certs_dir     = $dir/newcerts       # Directory for new certs
#crl_dir           = $dir/crl            # Where CRL (Certificate Revocation Lists) are stored
database          = $dir/index.txt      # The database file for issued certs
serial            = $dir/serial         # The current serial number file
private_key       = $dir/private/ca.key # The CA private key
certificate       = $dir/certs/ca.crt   # The CA certificate
#crlnumber         = $dir/crlnumber      # The current CRL number file
#crl               = $dir/crl/crl.pem    # The CRL file
#default_crl_days  = 30                  # How long before next CRL is generated
default_md        = sha256              # Default digest algorithm to sign certs


``` 

# cheatsheet
1. print everything about this certificate:
`openssl x509 -in mail.pem -noout -text`

2. create the easiest self-signed certificate: `openssl req -x509 -newkey rsa:4096 -keyout /etc/ssl/private/mail.key -out /etc/ssl/certs/mail.pem -days 365 -nodes`

3. print cert from some site: `openssl s_client -connect mail.example.com:993 -showcerts | openssl x509 -noout -text`



# what critical field means besides semanthic

if some extension with critical field cannot be understood by the system, the whole certifacte is rejected
