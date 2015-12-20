##############################################
#
##############################################
include $(TOPDIR)/rules.mk
# Nameand release number of this package
PKG_NAME:=greatwall/greatwallapp
PKG_RELEASE:=1

PKG_BUILD_DIR:= $(BUILD_DIR)/$(PKG_NAME)
 
 
include $(INCLUDE_DIR)/package.mk
 

define Package/greatwallapp
	SECTION:=greatwall app
	CATEGORY:=greatwall modules
	TITLE:=greatwall user support
	DEPENDS:=+libpthread
endef

define Build/Prepare
	rm -rf $(PKG_BUILD_DIR)
	mkdir -p $(PKG_BUILD_DIR)
	\$(CP) ./src/* $(PKG_BUILD_DIR)/
endef
define Package/greatwallapp/install
	#生成可执行文件目录
	$(INSTALL_DIR) $(1)/usr/greatwall/bin
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/model/cbi
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/view
	$(INSTALL_DIR) $(1)/usr/lib/lua/greatwall
	
	#安装
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/greatwallapp $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/greatwallcmd $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) ./files/greatwalldog $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/md5 $(1)/usr/greatwall/bin/
	$(INSTALL_BIN) ./files/etc/init.d/* $(1)/etc/init.d/
	$(INSTALL_CONF) ./files/etc/config/* $(1)/etc/config/
	#luci-greatwall	
	#lua modules
	$(INSTALL_BIN) ./files/luamodule/* $(1)/usr/lib/lua/greatwall
	
endef

$(eval $(call BuildPackage,greatwallapp))
