SPK_NAME = psqlodbc
SPK_VERS = 18.00.0006
SPK_REV = 1
SPK_ICON = src/psqlodbc.png

DEPENDS = cross/psqlodbc

MAINTAINER = Some Maintainer
DESCRIPTION = The official PostgreSQL ODBC driver, with the unixODBC driver manager. The drivers are registered as \"PostgreSQL Unicode\" and \"PostgreSQL ANSI\".
CHANGELOG = "Initial release of psqlODBC v18.00.0006 with unixODBC v2.3.14."

STARTABLE = no
DISPLAY_NAME = PostgreSQL ODBC Driver

HOMEPAGE = https://odbc.postgresql.org
LICENSE  = LGPLv2

SPK_COMMANDS = bin/isql bin/iusql bin/odbcinst

POST_STRIP_TARGET = psqlodbc_extra_install

include ../../mk/spksrc.spk.mk

.PHONY: psqlodbc_extra_install
# unixODBC reads the driver list from its sysconfdir, which is the package's etc folder
psqlodbc_extra_install:
	@install -d $(STAGING_DIR)/etc
	@install -m 644 src/odbcinst.ini $(STAGING_DIR)/etc/odbcinst.ini
