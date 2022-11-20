worker_processes 5; # default 1

events {
  worker_connections 2048; # default 1024
  multi_accept on; # default off
}

http {
  server_tokens off; # default on
  
  server {
    client_body_buffer_size 16k; # default 8k|16k
    client_body_timeout 12; # default 60s
    client_max_body_size 8m; # default 1m

    client_header_buffer_size 1k; # default 1k
    client_header_timeout 12; # default 60s

    keepalive_requests 1000; # default 1000
    keepalive_timeout 300; # default 75s

    send_timeout 10; # default 60
    
    # Prevent mobile providers modding site
    add_header "Cache-Control" "no-transform";
    
    # Indicates whether a browser should be allowed to render a page within the frame or iframe
    add_header X-Frame-Options SAMEORIGIN;
    
    # Enable HSTS
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload" always;
  }
}
