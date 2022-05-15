To get a PEM & TLSA DNS record that will work for [DANE SSL/TLS](https://en.wikipedia.org/wiki/DNS-based_Authentication_of_Named_Entities), do the following

- Edit the file `config` and put in the values you want (see `config.example`)
- run `./make_key`

This will give you two files - a PEM & a TXT of the DNS TLSA records. They will be prefixed by the host name

Give the PEM to your SSL/TLS server as *both* the certificate & key file, & put the DNS record in your server's parent DNS zone file (DNSSEC signed).

e.g for `nginx`

        ssl_certificate /etc/nginx/ca/dane.txt.pem;
        ssl_certificate_key /etc/nginx/ca/dane.txt.pem;


If you want to keep multiple copies of different `config` files, you can give them different names, then run

        ./make_key <config-file>

You can try out the example, if you wish - but it will only be useful if you happen to own the domain name `example.txt`

        ./make_key config.example
