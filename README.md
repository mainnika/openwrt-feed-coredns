# openwrt-feed-coredns

This is an openwrt feed that contains definitions to include CoreDNS software into your OpenWRT build.

## install from a binary

1. download an ipk file from the releases page https://code.tokarch.uk/mainnika/openwrt-feed-coredns/releases
2. put the file to the device, e.g. path `/tmp/coredns.ipk`
2. use opkg to install the downloaded file, e.g. `opkg install /tmp/coredns.ipk`

## how to add the feed into your build

1. open your feeds.conf.default and add the following line:

   `src-git feed_coredns https://code.tokarch.uk/mainnika/openwrt-feed-coredns.git`

2. run update script:

   `./scripts/feeds update feed_coredns`

3. install coredns packages into your build:

   `./scripts/feeds install -a -p feed_coredns`

> see for details: https://openwrt.org/docs/guide-developer/feeds

## service init

The package setups an init script `/etc/init.d/coredns` and uci config section:

```
config coredns 'main'
	option port '53'
	option config '/etc/coredns/Corefile'
```

There are two options defined:
- port, default: 53 -- a port where coredns will listen for connections
- config, default: /etc/coredns/Corefile -- a Corefile config file

> Use `uci` tool to change these values, e.g.: `uci set coredns.main.port=1053'

## coredns configuration

The package provides an empty config `Corefile` located at `/etc/coredns/Corefile`.
The empty `Corefile`:

```
. { }
```

