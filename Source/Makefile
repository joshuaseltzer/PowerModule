export ARCHS = arm64 armv7 arm64e

include $(THEOS)/makefiles/common.mk

BUNDLE_NAME = PowerModule
PowerModule_BUNDLE_EXTENSION = bundle
PowerModule_CFLAGS = -fobjc-arc -Iheaders
PowerModule_FILES = $(wildcard *.m)
PowerModule_LDFLAGS = Frameworks/ControlCenterUIKit.tbd
PowerModule_INSTALL_PATH = /Library/ControlCenter/Bundles/

THEOS_PACKAGE_BASE_VERSION = 1.3.1-cobra2168
_THEOS_INTERNAL_PACKAGE_VERSION = 1.3.1-cobra2168

include $(THEOS_MAKE_PATH)/bundle.mk

after-stage::
	chmod 4775 $(THEOS_STAGING_DIR)/usr/bin/mobileldrestart
	chmod 0775 layout/DEBIAN/postinst

after-install::
	install.exec "killall -9 backboardd"

SUBPROJECTS += powermoduleprefs
SUBPROJECTS += mobileldrestart
include $(THEOS_MAKE_PATH)/aggregate.mk
