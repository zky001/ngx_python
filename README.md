ngx_python
==========
[ngx_python](https://github.com/rryqszq4/ngx_python) - Embedded python for nginx-module. Another name is python-nginx-module.

Requirement
-----------
- python 2.7.*
- nginx-1.6.3+ 

Installation
-------
```sh
$ git clone https://github.com/rryqszq4/ngx_python.git

$ wget 'http://nginx.org/download/nginx-1.6.3.tar.gz'
$ tar -zxvf nginx-1.6.3.tar.gz
$ cd nginx-1.6.3

$ export PYTHON_INC=/path/to/python/include/python2.7
$ export PYTHON_BIN=/path/to/python/bin

$ ./configure --user=www --group=www \
              --prefix=/path/to/nginx \
              --add-module=/path/to/ngx_python
$ make
$ make install
```

Synopsis
--------

```nginx
user www www;
worker_processes  4;

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;
    
        location /content_by_python {
            content_by_python "
from time import time,ctime
import ngx

ngx.echo('Hello, ngx_python at ' + ctime(time()))
            ";
        }
    }
}
```

Copyright and License
---------------------
Copyright (c) 2016, rryqszq4
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this
  list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice,
  this list of conditions and the following disclaimer in the documentation
  and/or other materials provided with the distribution.

* Neither the name of ngx_py nor the names of its
  contributors may be used to endorse or promote products derived from
  this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

