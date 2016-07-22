 以容器方式部署在9.105上（docker run -d -p 4002:4000  jihchi/echo-server2），用于调试nginx配置文件，如nginx.conf配置：
                 # 登入
                location /signin {
                        proxy_pass http://127.0.0.1:4002;
                        proxy_redirect off;
                        proxy_set_header Host $host;
                        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
可以在网页上以json方式显示http请求头的信息。
 


# echo-server2

![screenshot](screenshot.jpg)

## Summary

An HTTP which responds with the request in JSON.

## Private Usage

```
npm install -g echo-server2
```

## Example

Start server
```
$ echo-server2 5000
listening on 5000...
```

Make your requests
```
$ curl http://localhost:5000/foo/bar
{
  "ip": "127.0.0.1",
  "method": "GET",
  "url": "/foo/bar",
  "body": "",
  "headers": {
    "user-agent": "curl/7.21.4 (universal-apple-darwin11.0) libcurl/7.21.4 OpenSSL/0.9.8x zlib/1.2.5",
    "host": "localhost:5000",
    "accept": "*/*"
  },
  "meta": {
    "total": 1,
    "live": 1
  }
}
```
## Command line arguments

```
  --verbose, -v log request data to the console
```

## Simulate delays

Include `/delay/<time in ms>` in the url

## Simulate non-200 status codes

Include `/status/<status code>` in the url

## Meta data

`total` number of requests sent to the server

`live` number of requests currently open on the server

# Stores metrics in MongoDB

Just set your `MONGOLAB_URI` env var and it will start storing `echo` documents

# Docker

[echo-server2](https://hub.docker.com/r/jihchi/echo-server2/)

```
$ docker run -p 4000:4000 echo-server2
```

<license()>
#### MIT License

Copyright &copy; 2016 Archie Lee &lt;achi@987.tw&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
</end>
