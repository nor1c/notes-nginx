**Core functionality** http://nginx.org/en/docs/ngx_core_module.html
**ngx_http_core_module** http://nginx.org/en/docs/http/ngx_http_core_module.html

<hr>

### `worker_processes` directive

Tells nginx how many processes or instances to fire-up when starting.
value `auto`: is not a default value, sets it to the number of the CPU cores available in the system

#### # Useful Commands

- `nproc` give a number of core of the CPU in the system
- `lscpu` give a detail about the processor in the system

<hr>

### `events.worker_connections` directive

Tells the processes how many request can be serve simultaneously. <br>
If we have **2 worker_processes** and you have **worker_connections** set to **1024**, that's equal to **2048 concurrent requests/total connections**,<br> formula: `worker_processes*worker_connections`

#### # Useful Commands

- `ulimit -n` "with a 'n' flag" help to get a value of worker_processes

<hr>

### `events.multi_accept` directive (default: on)

If `multi_accept` is disabled, a worker process will accept one new connection at a time. Otherwise, a worker process will accept all new connections at a time.

http://nginx.org/en/docs/ngx_core_module.html#multi_accept

<hr>

### `http.client_body_buffer_size`

Sets buffer size for reading client request body. In case the request body is larger than the buffer, the whole body or only its part is written to a temporary file. By default, buffer size is equal to two memory pages. This is 8K on x86, other 32-bit platforms, and x86-64. It is usually 16K on other 64-bit platforms.

<hr>

### `http.client_header_buffer_size`

Sets buffer size for reading client request header. _For most requests, a buffer of 1K bytes is enough._ However, if a request includes long cookies, or comes from a WAP client, it may not fit into 1K. If a request line or a request header field does not fit into this buffer then larger buffers, configured by the `large_client_header_buffers` directive, are allocated.

<hr>

### `http.client_max_body_size`

Sets the maximum allowed size of the client request body. If the size in a request exceeds the configured value, the **413 (Request Entity Too Large)** error is returned to the client. Please be aware that browsers cannot correctly display this error. Setting _size_ to 0 disables checking of client request body size.

<hr>

### Other useful directives

- `open_file_cache` http://nginx.org/en/docs/http/ngx_http_core_module.html#open_file_cache
