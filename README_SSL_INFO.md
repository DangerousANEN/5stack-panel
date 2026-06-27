## Notes on SSL
Currently, the external reverse proxy (NGINX on the jumphost) is only listening on port 80 for `cs2.zxc1x1.ru`. The internal Kubernetes cluster has generated local `mkcert` certificates for HTTPS, but since traffic is flowing through the external proxy first, the user's browser is expecting a valid CA-signed certificate (like Let's Encrypt).

The user must either bypass the warning manually ("Proceed to unsafe") or install Certbot on their jumphost to provision Let's Encrypt certs for `cs2.zxc1x1.ru` and `*.cs2.zxc1x1.ru`, and update their NGINX configuration accordingly.
