#
# Copyright (C) 2017 Hauke Mehrtens
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=arm-trusted-firmware-sunxi
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/apritzel/arm-trusted-firmware
PKG_SOURCE_DATE:=2018-02-04
PKG_SOURCE_VERSION:=ae78724247a01560164d607ed66db111c74d8df0
PKG_MIRROR_HASH:=e4ddc3294f86c1e163d683a2322427bbdd5b63762ead4b1792b34df75d7bda28

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=license.md

PKG_MAINTAINER:=Hauke Mehrtens <hauke@hauke-m.de>

include $(INCLUDE_DIR)/package.mk


define Package/arm-trusted-firmware-sunxi
    SECTION:=boot
    CATEGORY:=Boot Loaders
    TITLE:=ARM Trusted Firmware for Allwinner
    DEPENDS:=@TARGET_sunxi_cortexa53
endef

export GCC_HONOUR_COPTS=s

MAKE_VARS = \
	CROSS_COMPILE="$(TARGET_CROSS)"

MAKE_FLAGS += \
	PLAT=sun50iw1p1 \
	bl31

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)
	$(CP) $(PKG_BUILD_DIR)/build/sun50iw1p1/release/bl31.bin $(STAGING_DIR_IMAGE)/bl31.bin
endef

define Package/arm-trusted-firmware-sunxi/install
endef

$(eval $(call BuildPackage,arm-trusted-firmware-sunxi))
