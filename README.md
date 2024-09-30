<img width="437" alt="image" src="https://github.com/user-attachments/assets/cb4592a8-8408-4130-ae9d-21b4a17ad85d"><img width="437" alt="image" src="https://github.com/user-attachments/assets/ebacdfa7-4ce4-4d1e-834e-d3c722b64e51">Step1:
x509.genkey is located at /usr/src/linux/certs/x509.genkey.
[ req ]
default_bits = 4096
distinguished_name = req_distinguished_name
prompt = no
string_mask = utf8only
x509_extensions = myexts

[ req_distinguished_name ]
CN = Modules

[ myexts ]
basicConstraints=critical,CA:FALSE
keyUsage=digitalSignature
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid

Step2:
openssl req -new -nodes -utf8 -sha512 -days 36500 -batch -x509 -config x509.genkey -outform DER -out signing_key.x509 -keyout signing_key.pem
會產生 signing_key.pem signing_key.x509

Step3:
//mv signing_key.pem signing_key.x509 `find /usr/src/*-generic/certs`
mv signing_key.pem signing_key.x509 /lib/modules/xxxx/build/certs

<img width="437" alt="image" src="https://github.com/user-attachments/assets/a261ab3f-7497-4ac1-9913-167ff185d0f4">

