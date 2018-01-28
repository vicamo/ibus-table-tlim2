# ibus-table-tlim2 - The TLIM2 for IBus Tables.

m4_define([package_name], [ibus-table-tlim2])

AC_INIT([package_name],
	[1.0],
	[http://github.com/vicamo/ibus-table-tlim2/issues],
	[package_name],
	[http://github.com/vicamo/ibus-table-tlim2])

# AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])

AM_INIT_AUTOMAKE([1.14 dist-xz foreign subdir-objects no-define -Wall])
AM_MAINTAINER_MODE([enable])
AM_SILENT_RULES([yes])

# check for ibus-table-createdb
PKG_CHECK_MODULES([IBUS_TABLE], [ibus-table >= 1.1.0])
AC_ARG_VAR([IBUS_TABLE_CREATEDB],[[ibus-table-createdb, which generate db]])
AC_PATH_PROG([IBUS_TABLE_CREATEDB],[ibus-table-createdb],
        [AC_MSG_ERROR([ibus-table-createdb not found.])])

PKG_CHECK_VAR([IBUS_TABLE_DIR], [ibus-table], [tabledir], ,
	[AC_MSG_FAILURE([Unable to find value for tabledir])])
PKG_CHECK_VAR([IBUS_ICON_DIR], [ibus-table], [icondir], ,
	[AC_MSG_FAILURE([Unable to find value for icondir])])
AC_SUBST([IBUS_ICON_DIR])

# OUTPUT files
AC_CONFIG_FILES(
	Makefile
	tables/tlim2.txt
)

AC_OUTPUT

AC_MSG_RESULT([
Build options:
  Version                   $VERSION
  Install prefix            $prefix
])

