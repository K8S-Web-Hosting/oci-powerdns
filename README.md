# oci-powerdns
An OCI image for running PowerDNS using the Bind/named backend.

## How?

You can simply launch a container with:

```bash
docker run -it \
  -v "$LOCAL_ROOT/pdns:/etc/pdns" \
  -v "$LOCAL_ROOT/named.conf:/etc/named.conf" \
  -v "$LOCAL_ROOT/var-named/:/var/named" \
  -p 8053:53/tcp \
  -p 8053:53/udp \
  local/pdns
```

> Ensure you have properly set the `LOCAL_ROOT` variable to a folder where the files exist.

The necessary files to provide are:
* An `/etc/pdns` folder including `pdns.conf`.
* An `/etc/named.conf` file.
* The folder that houses all the named zonefiles.

The container will simply start pdns_server and nothing else.
If you need more feel free to use this as a base image and add your own entrypoint script.
Otherwise, once given the correct configs the PDNS service will start.
