# nginx\_cookie\_routing\_example

Here we show an example of how nginx can route to different hosts based
on the presence or absence of an HTTP cookie.

Using Docker Compose, we start two web servers, "static1" and "static2". They
each serve a simple html file identifying themselves.

We then start an nginx acting as a reverse proxy - with the nginx configuration
defined in `reverse_proxy.conf`.

You can validate behavior with curl:

```sh
# no cookie set
curl http://localhost:8080
<h1>static_1</h1>
```

```sh
# cookie set
curl --cookie MAGICCOOKIE=any_value http://localhost:8080
<h1>static_2</h1>
```
