PKG_NAME = libwebsockets
PKG_VERS = 1.4-chrome43-firefox-36
PKG_EXT = tar.gz
PKG_DIST_NAME = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = http://git.libwebsockets.org/cgi-bin/cgit/libwebsockets/snapshot
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

DEPENDS = cross/openssl

HOMEPAGE = http://libevent.org/
COMMENT  = An event notification library
LICENSE  = http://libevent.org/LICENSE.txt

CONFIGURE_TARGET = myConfigure
INSTALL_TARGET = myInstall

include ../../mk/spksrc.cross-cc.mk

.PHONY: myConfigure
myConfigure:
	$(RUN) cmake \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_PREFIX=$(INSTALL_PREFIX) \
		-DCMAKE_CROSSCOMPILING=TRUE \
		-DCMAKE_SYSTEM_NAME=Linux \
		-DCMAKE_C_COMPILER=$(TC_PATH)$(TC_PREFIX)gcc \
		-DCMAKE_EXE_LINKER_FLAGS="-L$(INSTALL_DIR)$(INSTALL_PREFIX)/lib -Wl,--rpath-link,$(INSTALL_DIR)$(INSTALL_PREFIX)/lib -Wl,--rpath,/usr/local/chromaprint/lib" \
		-DCMAKE_FIND_ROOT_PATH=$(INSTALL_DIR)$(INSTALL_PREFIX) \
		-DCMAKE_FIND_ROOT_PATH_MODE_PROGRAM=NEVER \
		-DCMAKE_FIND_ROOT_PATH_MODE_LIBRARY=ONLY \
		-DCMAKE_FIND_ROOT_PATH_MODE_INCLUDE=ONLY

.PHONY: myInstall
myInstall:
	$(RUN) $(MAKE) install DESTDIR=$(INSTALL_DIR)

