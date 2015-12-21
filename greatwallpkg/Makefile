##############################################
#
##############################################
include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk
PKG_NAME:=greatwall/greatwallpkg
PKG_RELEASE:=1

PKG_BUILD_DIR:= $(BUILD_DIR)/$(PKG_NAME)
 
 
include $(INCLUDE_DIR)/package.mk
 

define Package/greatwallpkg
	SECTION:=greatwall pkg
	CATEGORY:=greatwall modules
	TITLE:=greatwall user support
	DEPENDS:=+libpthread
endef

define Build/Prepare
	rm -rf $(PKG_BUILD_DIR)
	mkdir -p $(PKG_BUILD_DIR)
	\$(CP) ./src/* $(PKG_BUILD_DIR)/
endef
define Package/greatwallpkg/install
	#build dir
	echo $(LINUX_VERSION)============================================
	$(INSTALL_DIR) $(1)/usr/greatwall/bin
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/model/cbi
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/view
	$(INSTALL_DIR) $(1)/usr/lib/lua/greatwall
	$(INSTALL_DIR) $(1)/etc/modules.d/
	$(INSTALL_DIR) $(1)/etc/modules-boot.d/
	$(INSTALL_DIR) $(1)/lib/modules/$(LINUX_VERSION)/
	#setup
	$(INSTALL_BIN) ./files/greatwallapp $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) ./files/greatwallcmd $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) ./files/greatwalldog $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) ./files/md5 $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) ./files/etc/init.d/* $(1)/etc/init.d/
	$(INSTALL_CONF) ./files/etc/config/* $(1)/etc/config/
	#insert kmod
	$(INSTALL_BIN) ./ipkg/etc/modules.d/* $(1)/etc/modules.d/
	$(INSTALL_BIN) ./ipkg/etc/modules-boot.d/* $(1)/etc/modules-boot.d/
	$(INSTALL_BIN) ./ipkg/lib/modules/$(LINUX_VERSION)/* $(1)/lib/modules/$(LINUX_VERSION)/
	#luci-greatwall	
	
endef

$(eval $(call BuildPackage,greatwallpkg))
