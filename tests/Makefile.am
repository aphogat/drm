SUBDIRS = modeprint proptest

if HAVE_LIBKMS
SUBDIRS += kmstest modetest
endif

if HAVE_RADEON
SUBDIRS += radeon
endif

if HAVE_EXYNOS
SUBDIRS += exynos
endif

if HAVE_TEGRA
SUBDIRS += tegra
endif

if HAVE_LIBUDEV
SUBDIRS += vbltest
endif

AM_CFLAGS = \
	$(WARN_CFLAGS)\
	-I $(top_srcdir)/include/drm \
	-I $(top_srcdir)

LDADD = $(top_builddir)/libdrm.la

check_PROGRAMS = \
	dristat \
	drmstat

if HAVE_LIBUDEV

check_LTLIBRARIES = libdrmtest.la

libdrmtest_la_SOURCES = \
	drmtest.c \
	drmtest.h

LDADD += \
	libdrmtest.la \
	$(LIBUDEV_LIBS)


XFAIL_TESTS =					\
	auth					\
	lock

TESTS =						\
	openclose				\
	getversion				\
	getclient				\
	getstats				\
	setversion				\
	updatedraw				\
	name_from_fd

check_PROGRAMS += $(TESTS)

endif
