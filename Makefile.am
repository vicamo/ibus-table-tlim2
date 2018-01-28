ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}

EXTRA_DIST = \
  autogen.sh \
  INSTALL \
  README

BUILT_SOURCES =

GITIGNOREFILES = \
  $(DIST_ARCHIVES) \
  debian

CLEANFILES =
DISTCLEANFILES =

MAINTAINERCLEANFILES = \
  $(GITIGNORE_MAINTAINERCLEANFILES_TOPLEVEL) \
  $(GITIGNORE_MAINTAINERCLEANFILES_M4_LIBTOOL) \
  $(GITIGNORE_MAINTAINERCLEANFILES_MAKEFILE_IN) \
  $(srcdir)/INSTALL \
  $(srcdir)/README

DISTCHECK_CONFIGURE_FLAGS = \
  --disable-maintainer-mode

##############################
# table database

tablesdir = $(IBUS_TABLE_DIR)
tables_DATA = \
  tables/tlim2.db

.txt.db:
	@$(MKDIR_P) $(@D)
	$(IBUS_TABLE_CREATEDB) -n $@ -s $<

EXTRA_DIST += \
  tables/tlim2.bin \
  tables/tlim2.txt

CLEANFILES += \
  $(tables_DATA)

##############################
# icons

iconsdir = $(IBUS_ICON_DIR)
icons_DATA = \
  icons/tlim2.png

EXTRA_DIST += \
  $(icons_DATA)

##############################
# Additional clean steps

EXTRA_DIST += ChangeLog
BUILT_SOURCES += ChangeLog

distclean-local:
	if test "$(srcdir)" = "."; then :; else \
	  rm -f ChangeLog; \
	fi

ChangeLog:
	$(AM_V_GEN) if test -d "$(srcdir)/.git"; then \
	  (GIT_DIR=$(top_srcdir)/.git $(top_builddir)/build-aux/missing git log --stat) | fmt --split-only > $@.tmp \
	  && mv -f $@.tmp $@ \
	  || ($(RM) $@.tmp; \
	      echo Failed to generate ChangeLog, your ChangeLog may be outdated >&2; \
	      (test -f $@ || echo git-log is required to generate this file >> $@)); \
	else \
	  test -f $@ || \
	  (echo A git checkout and git-log is required to generate ChangeLog >&2 && \
	  echo A git checkout and git-log is required to generate this file >> $@); \
	fi

EXTRA_DIST += AUTHORS
BUILT_SOURCES += AUTHORS
AUTHORS:
	$(AM_V_GEN)if test -x "`which git 2>/dev/null`" -a -d "$(srcdir)/.git" ; then \
	  ( cd $(srcdir) ; \
	    echo "$(PACKAGE) -- authors file.  $(DATE)" ; \
	    echo "" ; \
	    git log|grep '^Author:'|awk '{if(!authors[$$0]){print$$0;authors[$$0]=1;}}' \
	  )>$@ ; \
	else touch $@ ; fi

CLEANFILES += $(BUILT_SOURCES)
GITIGNOREFILES += $(BUILT_SOURCES)

-include $(top_srcdir)/git.mk
