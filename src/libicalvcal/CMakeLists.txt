include_directories(
  ${CMAKE_BINARY_DIR}
  ${CMAKE_SOURCE_DIR}/src ${CMAKE_BINARY_DIR}/src
  ${CMAKE_SOURCE_DIR}/src/libicalss ${CMAKE_BINARY_DIR}/src/libicalss 
  ${CMAKE_SOURCE_DIR}/src/libical ${CMAKE_BINARY_DIR}/src/libical
  ${CMAKE_SOURCE_DIR}/src/libicalvcal ${CMAKE_BINARY_DIR}/src/libicalvcal
)

#these are generated sources, but we keep them in the repo
set(icalvcal_LIB_DEVSRCS vcc.c)

########### next target ###############

SET(icalvcal_LIB_SRCS
   icalvcal.h
   icalvcal.c
   port.h
   vcc.h
   vobject.h
   vobject.c
   vcaltmp.h
   vcaltmp.c
   ${icalvcal_LIB_DEVSRCS}
)

if(MSVC)
    list(APPEND icalvcal_LIB_SRCS ../icalvcal.def)
endif(MSVC)

add_library(icalvcal SHARED ${icalvcal_LIB_SRCS})

target_link_libraries(icalvcal ical)

set_target_properties(icalvcal PROPERTIES VERSION ${LIBICAL_LIB_VERSION_STRING} SOVERSION ${LIBICAL_LIB_MAJOR_VERSION})
install(TARGETS icalvcal ${INSTALL_TARGETS_DEFAULT_ARGS})

########### install files ###############

install(FILES
  icalvcal.h port.h vcc.h vobject.h vcaltmp.h
  DESTINATION
  ${INCLUDE_INSTALL_DIR}/libical)



#original Makefile.am contents follow:

#lib_LTLIBRARIES = libicalvcal.la
#
#INCLUDES =				\
#	-I$(top_srcdir)			\
#	-I$(top_srcdir)/src		\
#	-I$(top_builddir)/src		\
#	-I$(top_srcdir)/src/libical	\
#	-I$(top_builddir)/src/libical	\
#	-I$(top_srcdir)/src/libicalss
#
#libicalvcal_la_LDFLAGS = -version-info 43:0:43
#libicalvcal_la_LIBADD = ../libical/.libs/libical.la
#
#if DEV
#libicalvcal_la_DEVSOURCES = vcc.y
#else
#libicalvcal_la_DEVSOURCES = vcc.c
#endif
#
#
#libicalvcal_la_SOURCES =	\
#	icalvcal.h		\
#	icalvcal.c		\
#	port.h			\
#	vcc.h			\
#	vobject.h		\
#	vobject.c		\
#	vcaltmp.h		\
#	vcaltmp.c		\
#	$(libicalvcal_la_DEVSOURCES)
#
#libicalvcalincludedir = $(includedir)/libicalvcal
#
#libicalvcalinclude_HEADERS =	\
#	icalvcal.h		\
#	port.h			\
#	vcc.h			\
#	vobject.h		\
#	vcaltmp.h
#
#EXTRA_DIST =		\
#	README.TXT	\
#	vcaltest.c	\
#	vctest.c
#
