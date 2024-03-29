#
# Configuration file makefile for CUPS.
#
# Copyright © 2020-2024 by OpenPrinting.
# Copyright 2007-2015 by Apple Inc.
# Copyright 1993-2006 by Easy Software Products.
#
# Licensed under Apache License v2.0.  See the file "LICENSE" for more information.
#

include ../Makedefs

#
# Config files...
#

KEEP	=	cups-files.conf cupsd.conf snmp.conf
REPLACE	=	mime.convs mime.types


#
# Make everything...
#

all:


#
# Make library targets...
#

libs:


#
# Make unit tests...
#

unittests:


#
# Clean all config and object files...
#

clean:


#
# Dummy depend...
#

depend:


#
# Install all targets...
#

install:	all install-data install-headers install-libs install-exec


#
# Install data files...
#

install-data:
	for file in $(KEEP); do \
		if test -r $(SERVERROOT)/$$file ; then \
			$(INSTALL_CONFIG) -g $(CUPS_GROUP) $$file $(SERVERROOT)/$$file.N ; \
		else \
			$(INSTALL_CONFIG) -g $(CUPS_GROUP) $$file $(SERVERROOT) ; \
		fi ; \
		$(INSTALL_CONFIG) -g $(CUPS_GROUP) $$file $(SERVERROOT)/$$file.default; \
	done
	$(INSTALL_DIR) -m 755 $(DATADIR)/mime
	for file in $(REPLACE); do \
		if test -r $(DATADIR)/mime/$$file ; then \
			$(MV) $(DATADIR)/mime/$$file $(DATADIR)/mime/$$file.O ; \
		fi ; \
		if test -r $(SERVERROOT)/$$file ; then \
			$(MV) $(SERVERROOT)/$$file $(DATADIR)/mime/$$file.O ; \
		fi ; \
		$(INSTALL_DATA) $$file $(DATADIR)/mime ; \
	done
	-if test x$(PAMDIR) != x; then \
		$(INSTALL_DIR) -m 755 $(BUILDROOT)$(PAMDIR); \
		if test -r $(BUILDROOT)$(PAMDIR)/cups ; then \
			$(INSTALL_DATA) $(PAMFILE) $(BUILDROOT)$(PAMDIR)/cups.N ; \
		else \
			$(INSTALL_DATA) $(PAMFILE) $(BUILDROOT)$(PAMDIR)/cups ; \
		fi ; \
	fi


#
# Install programs...
#

install-exec:


#
# Install headers...
#

install-headers:


#
# Install libraries...
#

install-libs:


#
# Uninstall files...
#

uninstall:
	for file in $(KEEP) $(REPLACE) cupsd.conf.default; do \
		$(RM) $(SERVERROOT)/$$file; \
	done
	-$(RMDIR) $(SERVERROOT)
	for file in $(REPLACE); do \
		$(RM) $(DATADIR)/mime/$$file; \
	done
	-$(RMDIR) $(DATADIR)/mime
	-if test x$(PAMDIR) != x; then \
		$(RM) $(BUILDROOT)$(PAMDIR)/cups; \
		$(RMDIR) $(BUILDROOT)$(PAMDIR); \
	fi
