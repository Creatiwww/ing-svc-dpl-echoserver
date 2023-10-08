# echo-server

This is a python socket server that echos back any http request made to it.

## Example
Make a custom request:
```
$ curl --header "Favorite-Color: Purple" \
      --data "param1=value1&param2=value2"\
      http://localhost:5000/hello-mars
```

Prints:
```
$ python echo.py
Echoing from http://localhost:5000
127.0.0.1 - Thu Mar 15 23:43:27 2018 - POST /hello-mars HTTP/1.1
```

Returns
```
POST /hello-mars HTTP/1.1
Host: localhost:5000
User-Agent: curl/7.54.0
Accept: */*
Favorite-Color: Purple
Content-Length: 27
Content-Type: application/x-www-form-urlencoded

param1=value1&param2=value2
```

## Requirements

Python 3.4+

No other dependencies


## Running

Default port is 5000 (echo on a dialpad)

Python:
```
./echo.py
```

**Or:**

Docker:
```
docker build -t echo-server:latest .
docker run -itp 5000:5000 echo-server:latest
# test
curl -XPOST http://localhost:5000/ -d '{"Hello":"World!"}'
```


### Options
```
  -b BIND, --bind BIND  host to bind to
  -p PORT, --port PORT  port to listen on
  -v, --verbose         print all requests to terminal
```


## Build and push
```
  docker build -t echo-server:latest .
  docker tag echo-server:latest creatiwww/echo-server:latest
  docker push creatiwww/echo-server:latest
```