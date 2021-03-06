SPK_NAME = owncloud
SPK_VERS = 6.0.2
SPK_REV = 3
SPK_ICON = src/owncloud.png
DSM_UI_DIR = app

DEPENDS  = cross/busybox cross/$(SPK_NAME)

MAINTAINER = SynoCommunity
DESCRIPTION = ownCloud is a personal cloud which runs on your own server and gives you freedom and control over your own data.
ADMIN_URL = /owncloud/
RELOAD_UI = yes
DISPLAY_NAME = ownCloud
CHANGELOG = "1. DSM 5.0 compatibility"

HOMEPAGE   = http://owncloud.org/
LICENSE    = AGPL

WIZARDS_DIR = src/wizard/

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh

INSTALL_DEP_SERVICES = apache-web mysql
START_DEP_SERVICES = apache-web mysql
INSTUNINST_RESTART_SERVICES = apache-web

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

POST_STRIP_TARGET = owncloud_extra_install

BUSYBOX_CONFIG = daemon nice
ENV += BUSYBOX_CONFIG="$(BUSYBOX_CONFIG)" 

include ../../mk/spksrc.spk.mk

.PHONY: owncloud_extra_install
owncloud_extra_install: 
	install -m 755 -d $(STAGING_DIR)/var
	install -m 755 src/owncloud.sh $(STAGING_DIR)/bin/
	install -m 755 -d $(STAGING_DIR)/app
	install -m 644 src/app/config $(STAGING_DIR)/app/config
	install -m 644 src/autoconfig.php $(STAGING_DIR)/share/$(SPK_NAME)/config/autoconfig.php
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48; do \
		convert $(SPK_ICON) -thumbnail $${size}x$${size} \
		        $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done
