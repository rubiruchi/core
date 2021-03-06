# CORE
# (c)2012 the Boeing Company.
# See the LICENSE file included in this directory.
#
# author: Jeff Ahrenholz  <jeffrey.m.ahrenholz@boeing.com>
#
# Makefile for building corens3 components.
#

if WANT_PYTHON

SETUPPY	= setup.py
SETUPPYFLAGS = -v

# Python package build
noinst_SCRIPTS = build
build:
	$(PYTHON) $(SETUPPY) $(SETUPPYFLAGS) build

# Python package install
install-exec-hook:
	$(PYTHON) $(SETUPPY) $(SETUPPYFLAGS) install \
		--root=/$(DESTDIR) \
		--prefix=$(prefix) \
		--install-lib=$(pythondir) \
		--single-version-externally-managed \
		--no-compile

# Python package uninstall
uninstall-hook:
	-rm -rf core_ns3.egg-info
	-rm -rf $(DESTDIR)/$(pythondir)/core_ns3-$(PACKAGE_VERSION)-py$(PYTHON_VERSION).egg-info
	-rm -rf $(DESTDIR)/$(pythondir)/corens3
	-rm -rf $(DESTDIR)/$(datadir)/corens3

# Python package cleanup
clean-local:
	-rm -rf build

# because we include entire directories with EXTRA_DIST, we need to clean up
# the source control files
dist-hook:
	-rm -rf `find $(distdir)/ -name '*.pyc'`

distclean-local:
	-rm -rf core_ns3.egg-info

DISTCLEANFILES = Makefile.in 

# files to include with distribution tarball
EXTRA_DIST = LICENSE $(SETUPPY) corens3 examples

endif
# endif WANT_PYTHON
