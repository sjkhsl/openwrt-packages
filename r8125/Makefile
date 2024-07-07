#
# Download realtek r8125 linux driver from official site:
# https://www.realtek.com/Download/List?cate_id=584
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=r8125
PKG_VERSION:=9.013.02
PKG_RELEASE:=2

PKG_BUILD_DIR:=$(KERNEL_BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define KernelPackage/r8125
  TITLE:=Driver for Realtek r8125 chipsets
  SUBMENU:=Network Devices
  VERSION:=$(LINUX_VERSION)+$(PKG_VERSION)-$(PKG_RELEASE)
  DEPENDS:=@PCI_SUPPORT +kmod-mii +kmod-phy-realtek
  FILES:= $(PKG_BUILD_DIR)/r8125.ko
  AUTOLOAD:=$(call AutoProbe,r8125)
endef

define Package/r8125/description
  This package contains a driver for Realtek r8125 chipsets.
endef

define Build/Compile
	$(KERNEL_MAKE) M=$(PKG_BUILD_DIR) modules
endef

$(eval $(call KernelPackage,r8125))
