lib_LTLIBRARIES = libicalvcal.la

INCLUDES =				\
	-I$(top_srcdir)			\
	-I$(top_srcdir)/src		\
	-I$(top_builddir)/src		\
	-I$(top_srcdir)/src/libical	\
	-I$(top_builddir)/src/libical	\
	-I$(top_srcdir)/src/libicalss

libicalvcal_la_LDFLAGS = -version-info 43:0:43
libicalvcal_la_LIBADD = ../libical/.libs/libical.la

if DEV
libicalvcal_la_DEVSOURCES = vcc.y
else
libicalvcal_la_DEVSOURCES = vcc.c
endif


libicalvcal_la_SOURCES =	\
	icalvcal.h		\
	icalvcal.c		\
	port.h			\
	vcc.h			\
	vobject.h		\
	vobject.c		\
	vcaltmp.h		\
	vcaltmp.c		\
	$(libicalvcal_la_DEVSOURCES)

libicalvcalincludedir = $(includedir)/libical

libicalvcalinclude_HEADERS =	\
	icalvcal.h		\
	port.h			\
	vcc.h			\
	vobject.h		\
	vcaltmp.h

EXTRA_DIST =		\
	README.TXT	\
	vcaltest.c	\
	vctest.c

