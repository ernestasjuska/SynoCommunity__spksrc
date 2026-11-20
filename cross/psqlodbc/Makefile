PKG_NAME = psqlodbc
PKG_VERS = 18.00.0006
PKG_TAG = REL-$(subst .,_,$(PKG_VERS))
PKG_EXT = tar.gz
PKG_DIST_NAME = $(PKG_TAG).$(PKG_EXT)
PKG_DIST_SITE = https://github.com/postgresql-interfaces/psqlodbc/archive/refs/tags
PKG_DIST_FILE = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIR = $(PKG_NAME)-$(PKG_TAG)

DEPENDS = cross/unixodbc cross/libpq

HOMEPAGE = https://odbc.postgresql.org
COMMENT  = The official PostgreSQL ODBC driver.
LICENSE  = LGPLv2

GNU_CONFIGURE = 1
PRE_CONFIGURE_TARGET = psqlodbc_pre_configure

# odbc_config of the target cannot run on the build host, so configure gets a stand-in
ODBC_CONFIG_STUB = $(WORK_DIR)/odbc_config
CONFIGURE_ARGS  = --with-unixodbc=$(ODBC_CONFIG_STUB)
CONFIGURE_ARGS += --with-libpq=$(STAGING_INSTALL_PREFIX)

include ../../mk/spksrc.cross-cc.mk

.PHONY: psqlodbc_pre_configure
# Only releases up to 16.00 have source tarballs with configure; the git tag needs autoreconf.
psqlodbc_pre_configure:
	$(RUN) autoreconf --install
	@printf '#!/bin/sh\ncase "$$1" in\n  --include-prefix) echo "%s" ;;\n  --lib-prefix) echo "%s" ;;\n  --libs) echo "-L%s -lodbc" ;;\nesac\n' \
		"$(STAGING_INSTALL_PREFIX)/include" "$(STAGING_INSTALL_PREFIX)/lib" "$(STAGING_INSTALL_PREFIX)/lib" > $(ODBC_CONFIG_STUB)
	@chmod +x $(ODBC_CONFIG_STUB)
