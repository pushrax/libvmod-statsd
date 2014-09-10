AM_CPPFLAGS = @VMOD_INCLUDES@

vmoddir = @VMOD_DIR@
vmod_LTLIBRARIES = libvmod_statsd.la

libvmod_statsd_la_LDFLAGS = -module -export-dynamic -avoid-version

libvmod_statsd_la_SOURCES = \
	vcc_if.c \
	vcc_if.h \
	vmod_statsd.c

vcc_if.c vcc_if.h: @VMODTOOL@ $(top_srcdir)/$(DIR_PREFIX)src/vmod_statsd.vcc
	@VMODTOOL@ $(top_srcdir)/$(DIR_PREFIX)src/vmod_statsd.vcc

VMOD_TESTS = tests/*.vtc
.PHONY: $(VMOD_TESTS)

tests/*.vtc:
	@VARNISHTEST@ -Dvarnishd=@VARNISHD@ -Dvmod_topbuild=$(abs_top_builddir) $@

check: $(VMOD_TESTS)

EXTRA_DIST = \
	vmod_statsd.vcc \
	$(VMOD_TESTS)

CLEANFILES = $(builddir)/vcc_if.c $(builddir)/vcc_if.h \
	$(builddir)/vmod_statsd.man.rst \
	$(builddir)/vmod_statsd.rst \
	$(builddir)/../vmod_statsd.3