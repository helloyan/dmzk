include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=usb-serial-ch9344
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/$(PKG_NAME)
    SUBMENU:=USB Support
    TITLE:=Support for CH9344 devices
    FILES:=$(PKG_BUILD_DIR)/ch9344.ko
    DEPENDS:=kmod-usb-serial
    AUTOLOAD:=$(call AutoProbe,ch9344)
endef

define KernelPackage/$(PKG_NAME)/description
    Kernel support for Winchiphead CH9344 USB-to-Serial converters
endef

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(BUILDFLAGS)" \
		modules
endef

$(eval $(call KernelPackage,$(PKG_NAME)))
