
CN= itzroks-6630025ezu-jngiqba.us-south.containers.appdomain.cloud

man openssl-x509
      openssl x509 -req -in req.pem -CA cacert.pem -CAkey key.pem -CAcreateserial

       openssl x509 -in cert.pem -noout -text

       Display the "Subject Alternative Name" extension of a certificate:

        openssl x509 -in cert.pem -noout -ext subjectAltName

man openssl-req
        openssl genrsa -out key.pem 2048
        openssl req -new -key key.pem -out req.pem
