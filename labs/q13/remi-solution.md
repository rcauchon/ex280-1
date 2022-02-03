
Techzone.com
 CN= itzroks-6630025ezu-jngiqb.us-south.containers.appdomain.cloud

## Generate a Certificate Authority key (.key) 2048
openssl genrsa -des3 -out myCA.key 2048 
 
## Sign the CA certificate authority (.key)
openssl req -x509 -new -nodes -key myCA.key -out myCA.pem -days 3650 -sha256

## Enter  Common name : www.ibm.com

## Generate a private key tls for application
openssl genrsa -out quotes.key 2048

## Certificate Signing request (csr)
openssl req -new -key quotes.key -out quotes.csr

## Self sign the certificate
openssl x509 -req -in quotes.csr -CA myCA.pem -CAkey myCA.key -CAcreateserial -out quotes.crt -days 1650 -sha256

## Create the route Edge for the quotes service
oc create route edge quotes-https --service=quotes --ca-cert=./myCA.pem --cert=./quotes.crt --key=./quotes.key 
