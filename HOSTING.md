# Self-Hosting

[esm.sh](https://esm.sh) provides a fast, global content delivery network
publicly which powered by [Cloudflare](https://cloudflare.com). You may also want to
host esm.sh by yourself.

To serve esm.sh, You will need [Go](https://golang.org/dl) 1.16+ to
run and compile the server. The server runtime will install the nodejs (16 LTS)
automatically.

## Clone code

```baseh
git clone https://github.com/ije/esm.sh
cd esm.sh
```

## Run the sever locally

```bash
go run main.go --port=8080 --dev
```

Then you can import `React` from http://localhost:8080/react

## Deploy to remote host

Please ensure the [supervisor](http://supervisord.org/) has been installed on
your host machine.

```bash
./scripts/deploy.sh --init
```

Server options:

- `port` - the port to listen
- `httpsPort` - the port to listen https (use [autocert](golang.org/x/crypto/acme/autocert))
- `etcDir` - the etc directory (default is `/etc/esmd`)
- `cache` - the cache config (default is `memory:main`)
- `db` - the database config (default is `postdb:$etcDir/esm.db`)
- `fs` - the fs (storage) config (default is `local:$etcDir/storage`)
- `origin` - the origin of the CDN (this is useful when running the server behind a proxy/CDN, optional)
- `npmRegistry` - the npm registry (default is https://npmjs.org/registry)
- `npmToken` - the private token for npm registry (optional)

## Deploy with Docker

An example [Dockerfile](./Dockerfile) is found in the root of this project.
