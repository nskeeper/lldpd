AM_CFLAGS = -I $(top_srcdir)/include $(LLDP_CFLAGS)
AM_CPPFLAGS = $(LLDP_CPPFLAGS)
AM_LDFLAGS = $(LLDP_LDFLAGS)

lib_LTLIBRARIES = liblldpctl.la
include_HEADERS = lldpctl.h

noinst_LTLIBRARIES = libfixedpoint.la
libfixedpoint_la_SOURCES = fixedpoint.h fixedpoint.c

liblldpctl_la_SOURCES = \
	lldpctl.h atom.h errors.c connection.c atom.c helpers.c helpers.h \
	atoms/config.c atoms/dot1.c atoms/dot3.c \
	atoms/interface.c atoms/med.c atoms/mgmt.c atoms/port.c \
	atoms/custom.c
liblldpctl_la_LIBADD  = $(top_builddir)/src/libcommon-daemon-lib.la libfixedpoint.la
liblldpctl_la_LDFLAGS = $(AM_LDFLAGS) -export-symbols-regex '^lldpctl_' -version-info 10:0:6

# -version-info format is `current`:`revision`:`age`. For more details, see:
#   http://sources.redhat.com/autobook/autobook/autobook_91.html#SEC91

pkgconfig_DATA = lldpctl.pc

TEMPLATES  = lldpctl.pc
EXTRA_DIST = lldpctl.pc.in
CLEANFILES = $(TEMPLATES)
lldpctl.pc: lldpctl.pc.in
include $(top_srcdir)/edit.am
