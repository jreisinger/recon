Recon is a CLI tool (and a Go package) for gathering public information about network hosts. It's fast, easy to use, and easy to extend.

Installation on your machine (assuming you have Go [installed](https://go.dev/doc/install))

```
go install github.com/jreisinger/recon/cmd/recon@latest
```

Installation inside an ephemeral container

```
$ docker run --rm -it golang /bin/bash

# go install github.com/jreisinger/recon/cmd/recon@latest
```

Usage

```
$ recon example.com
example.com: ip addreses (ips): 93.184.216.34, 2606:2800:220:1:248:1893:25c8:1946
example.com: name servers (ns): a.iana-servers.net, b.iana-servers.net
example.com: txt records (txt): v=spf1 -all, wgyf8z8cgvm2qmxpnbnldrcltvk4xqfn
example.com: geolocation (geo): 93.184.216.34: New York - US, 2606:2800:220:1:248:1893:25c8:1946: New York - US
example.com: http version (httpver): HTTP/2.0
example.com: open tcp ports (ports): 80, 443
example.com: certificate authority (ca): DigiCert Inc
example.com: certificate issuer (iss): DigiCert Inc
example.com: tls version (tlsver): TLS 1.3

$ echo -e "example.com\nexample.net\nexample.org" | recon -r ips -j
{"target":"example.com","desc":"ip addreses (ips)","results":["93.184.216.34"]}
{"target":"example.net","desc":"ip addreses (ips)","results":["93.184.216.34"]}
{"target":"example.org","desc":"ip addreses (ips)","results":["93.184.216.34"]}
```
