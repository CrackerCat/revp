# revp
### Build
Run `make` and then use the resulting executable `revp.exe`.
### Instructions
There are 3 components to revp: `server`, `client`, and `proxy connections`.

`Server` listens for `client` and starts listening for `proxy connections` once `client` connects.

All `proxy connection` requests are routed to the `client` through the `server`.

What makes this a "reverse" proxy is the fact that the `client` initiates connection to the `server`, so there's no need to open ports or write firewall rules for the `client` whose network access you want to reach into -- you can basically run this on any network node whose firewall allows outbound traffic to your `server` port (essentially most firewall configurations found in the wild allow all outbound traffic).

`Proxy connections` are expected to make a first request of HTTP CONNECT and once connected they can exchange any data of any protocol with the destination address:port requested in the HTTP CONNECT. `Server` transparently routes all traffic from and to `client` and `client` routes all traffic from and to the remote destination.
### Options
Options:
```Options:
  -h [ --help ]              Help screen
  -s [ --server ]            Starts revp in server mode
  -c [ --client ]            Starts revp in client mode
  -l [ --clientPort ] arg    [Server mode] Port that listens for client
  -p [ --proxyPort ] arg     [Server mode] Port that listens for proxy 
                             connections
  -a [ --serverAddress ] arg [Client mode] Address of server
  -z [ --serverPort ] arg    [Client mode] Port of server
```
