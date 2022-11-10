```
server {
  listen 80;
  server_name ~^(www\.|)docker.domain_name$;
  return 301 https://docker.domain_name;
}

server {
  listen 443 ssl;
  listen [::]:443 ipv6only=on;
  server_name ~^(www\.|)docker.domain_name$;

  # SSL
  ssl_certificate /etc/nginx/ssl/docker.domain_name/fullchain.pem;
  ssl_certificate_key /etc/nginx/ssl/docker.domain_name/privkey.pem;
  
  # Recommendations from https://raymii.org/s/tutorials/Strong_SSL_Security_On_nginx.html
  ssl_protocols TLSv1.1 TLSv1.2;
  ssl_ciphers 'EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH';
  ssl_prefer_server_ciphers on;
  ssl_session_cache shared:SSL:10m;

  # Avoid HTTP 413 for large image uploads
  client_max_body_size 0;

  # Avoid HTTP 411
  chunked_transfer_encoding on;

  location / {
    proxy_pass                          http://localhost:5000;
    proxy_set_header  Host              $host;  
    proxy_set_header  X-Real-IP         $remote_addr; 
    proxy_set_header  X-Forwarded-For   $proxy_add_x_forwarded_for;
    proxy_set_header  X-Forwarded-Proto $scheme;
    proxy_read_timeout                  900;
  }
}
```
