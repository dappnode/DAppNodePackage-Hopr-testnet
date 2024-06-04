# Repository structure

There are three repositories:

- official: https://github.com/dappnode/DAppNodePackage-Hopr
- internal: https://github.com/hoprnet/DAppNodePackage-Hopr
- testnet: https://github.com/dappnode/DAppNodePackage-Hopr-Testnet

The `internal` is a fork of the `official` one.  The `testnet` repo is configured specifically to use our `rotsee` testnet

All PRs are built and packages are uploaded to IPFS for testing. Changes to the
branches `main` and `release` are built and packaged as well.
 
# Development process

Clone the repo

```sh
git clone git@github.com:hoprnet/DAppNodePackage-Hopr-Testnet.git
```

Build a package with (requires Node.js)

```sh
npx @dappnode/dappnodesdk build
```

This should create output similar to

```
  ✔ Verify connection
  ✔ Verify connection
  ✔ Create release dir
  ✔ Validate files
  ✔ Copy files
  ✔ Build architecture linux/amd64
  ✔ Upload release to IPFS node
  ✔ Save upload results

  DNP (DAppNode Package) built and uploaded 
  Release hash : /ipfs/QmdZHJPrTJQZRr9gJKhQKXVSVSRf3jdBj6LqbZuZ8MNSWF
  http://my.dappnode/installer/public/%2Fipfs%2FQmdZHJPrTJQZRr9gJKhQKXVSVSRf3jdBj6LqbZuZ8MNSWF
```

### Grafana dashboard upgrades

When upgrading the Grafana dashboards, make sure:

- the file is called `hopr-testnet-public-grafana-dashboard.json`
- the `uid` property is non-empty and starts with `hopr-testnet-public-`

# Debugging

When connected to a DAppnode system, follow the link and install the package. If it is a development build, make sure to disable signature verification before installing the package.

![howto](bypass_signature_check.png)

# Useful links

- [Official documentation](https://docs.dappnode.io/docs/dev)
- [http://my.dappnode/public-packages](http://my.dappnode/public-packages) lists installed public packages
- [http://my.dappnode/package-manifest/hopr-testnet.public.dappnode.eth](http://my.dappnode/package-manifest/hopr-testnet.public.dappnode.eth) gets the internal view of the package metadata

When running with the [DMS package](http://my.dappnode/installer/dnp/dms.dnp.dappnode.eth) (Grafana, Loki, Prometheus):

- [http://prometheus.dms.dappnode:9090/targets](http://prometheus.dms.dappnode:9090/targets) lists Prometheus targets. Make sure the package's target is available

Automatic import of Prometheus targets is only available if `prometheusTargets` and automatic import of Grafana dashboards is only available if `grafanaDashboards` is present in the observed [package manifest](http://my.dappnode/package-manifest/hopr-testnet.public.dappnode.eth).
