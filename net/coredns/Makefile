include $(TOPDIR)/rules.mk

PKG_NAME:=coredns
PKG_VERSION:=1.8.6
PKG_RELEASE:=1

PKG_SOURCE:=coredns-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://codeload.github.com/coredns/coredns/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=cbe3764afe2148b8047ea7e5cbba5108c298dee3a9a0391028e2980e35beaa2b

PKG_MAINTAINER:=Nikita Tokarchuk <nikita@tokarch.uk>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/coredns/coredns
GO_PKG_LDFLAGS:=-s -w
GO_PKG_LDFLAGS_X:=github.com/coredns/coredns/coremain.GitCommit=13a9191efb0574cc92ed5ffd55a1f144b840d668

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/coredns
	SECTION:=net
	CATEGORY:=Network
	TITLE:=CoreDNS
	URL:=https://github.com/coredns/coredns
	DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle +libc +libpthread
endef

define Package/coredns/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))

	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/coredns $(1)/usr/sbin/

	$(INSTALL_DIR) $(1)/etc/coredns
	$(INSTALL_CONF) ./files/Corefile $(1)/etc/coredns/Corefile
endef

define Package/coredns/description
	CoreDNS is a DNS server that chains plugins.
endef

$(eval $(call GoBinPackage,coredns))
$(eval $(call BuildPackage,coredns))
