# DevOps Belfast - The Kong API Gateway
Hi all, I (@erran) wrote a [Kong][] presentation recently as a quick talk for DevOps Belfast.

## Pre-requisites
1. Run the `kong-database` and `kong` [docker containers](https://getkong.org/install/docker/).
2. Install [kongfig][] (e.g. `npm install -g kongfig`).
3. Profit! :tada:

## Demo code
The config.yml file committed in to this repository can be used with [kongfig][] from the initial commit on to perform each step of the demo.

Use `kongfig apply --host 127.0.0.1:8001 --path config.yml` from the root of this repository on any given commit to perform the demo step.

### Examples
#### Unauthenticated
```
$ curl -i http://127.0.0.1:8000/canary

HTTP/1.1 401 Unauthorized
Date: Tue, 27 Jun 2017 14:49:14 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
WWW-Authenticate: Basic realm="kong"
Server: kong/0.10.3

{"message":"Unauthorized"}
```

#### Bad credentials
```
$ curl -i -u invalid-user:invalid-pass http://127.0.0.1:8000/canary

HTTP/1.1 403 Forbidden
Date: Tue, 27 Jun 2017 14:49:28 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
Server: kong/0.10.3

{"message":"Invalid authentication credentials"}
```

#### Invalid credentials (outside of ACL)
```
$ curl -i -u jdoe:OpenSesame http://127.0.0.1:8000/canary

HTTP/1.1 403 Forbidden
Date: Tue, 27 Jun 2017 14:49:40 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
Server: kong/0.10.3

{"message":"You cannot consume this service"}
```

#### Valid credentials
```
$ curl -i -u jsmith:OpenSesame http://127.0.0.1:8000/canary

HTTP/1.1 200 OK
Date: Tue, 27 Jun 2017 14:49:45 GMT
Content-Type: text/html; charset=UTF-8
Content-Length: 1321
```

[kongfig]: https://github.com/mybuilder/kongfig
[Kong]: https://getkong.org
