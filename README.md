# openwrt-feed-coredns

This is an openwrt feed that contains definitions to include CoreDNS software into your OpenWRT build.

## how to add the feed into your build

> see for details: https://openwrt.org/docs/guide-developer/feeds

1. open your feeds.conf.default and add the following line:

   `src-git feed_coredns https://code.tokarch.uk/mainnika/openwrt-feed-coredns.git`

2. run update script:

   `./scripts/feeds update feed_coredns`

3. install coredns packages into your build:

   `./scripts/feeds install -a -p feed_coredns`
