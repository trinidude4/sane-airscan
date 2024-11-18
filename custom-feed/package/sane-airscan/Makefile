include $(TOPDIR)/rules.mk

PKG_NAME:=sane-airscan
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/alexpevzner/sane-airscan.git
PKG_SOURCE_VERSION:=7a88b37
PKG_SOURCE_DATE:=2024-11-18
PKG_VERSION:=$(PKG_SOURCE_DATE)

PKG_MAINTAINER:=alexpevzner <example@example.com>
PKG_LICENSE:=GPL-3.0

PKG_INSTALL:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/sane-airscan
  TITLE:=SANE - universal driver for eSCL and WSD
  URL:=https://github.com/alexpevzner/sane-airscan
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libsane +libjpeg-turbo +libpng +libavahi-client +libxml2 +gnutls-utils +libtiff
endef

define Package/sane-airscan/description
  AirScan (eSCL) and WSD SANE backend
endef

define Package/sane-airscan/conffiles
  /etc/sane.d/airscan.conf
endef

define Package/sane-airscan/install
	$(INSTALL_DIR) $(1)/etc/sane.d
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/etc/sane.d/airscan.conf $(1)/etc/sane.d/
	$(INSTALL_DIR) $(1)/etc/sane.d/dll.d
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/etc/sane.d/dll.d/airscan $(1)/etc/sane.d/dll.d/
	$(INSTALL_DIR) $(1)/usr/lib/sane
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/sane/libsane-airscan.so.* $(1)/usr/lib/sane/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/airscan-discover $(1)/usr/bin/
endef

$(eval $(call BuildPackage,sane-airscan))
