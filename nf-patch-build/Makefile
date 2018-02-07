TOPDIR:=..
SCRIPT_DIR:=$(TOPDIR)/scripts
DL_DIR:=$(TOPDIR)/dl
CONFIG_LINUX_4_9:=y


PKG_NAME:=iptables
PKG_VERSION:=1.6.1
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.netfilter.org/iptables
PKG_SOURCE_VERSION:=7df66f1c13563cfbab75246b009ce36f69ee4487
PKG_MIRROR_HASH:=22f15ef41fd8e3724bedcee666b7b6a3491d2d038d580ef1fb032718dcb73f14

PKG_FIXUP:=autoreconf

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2.0
PKG_CPE_ID:=cpe:/a:netfilter_core_team:iptables


include $(TOPDIR)/include/download.mk

all:
	if [ ! -e "$(DL_DIR)/$(PKG_SOURCE)" ] ; then  TOPDIR="$(TOPDIR)" $(SCRIPT_DIR)/download.pl $(DL_DIR) $(PKG_SOURCE) $(PKG_MD5SUM)  $(PKG_SOURCE)  $(PKG_SOURCE_URL) ; fi ; 
	cp $(DL_DIR)/$(PKG_SOURCE) . 
	tar xf $(PKG_SOURCE)
	rm -rf *.bz2 *.xz
	mv iptables* iptables
	$(SCRIPT_DIR)/patch-kernel.sh iptables $(TOPDIR)/package/network/utils/iptables/patches/
	echo $(TOPDIR)/package/network/utils/iptables/patches/ > iptables-patch-dir
