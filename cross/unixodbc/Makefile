PKG_NAME = unixODBC
PKG_VERS = 2.3.14
PKG_EXT = tar.gz
PKG_DIST_NAME = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = https://www.unixodbc.org
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

DEPENDS =

HOMEPAGE = https://www.unixodbc.org
COMMENT  = ODBC driver manager for unix, with the isql and odbcinst command line tools.
LICENSE  = LGPLv2.1+

GNU_CONFIGURE = 1
CONFIGURE_ARGS  = --disable-static
CONFIGURE_ARGS += --enable-gui=no

include ../../mk/spksrc.cross-cc.mk
