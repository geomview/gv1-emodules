AC_PREREQ(2.59)
AC_INIT(gvemodules-xforms, [0.1], Claus-Justus Heine <Claus.Heine@Mathematik.Uni-Freiburg.DE>)
AC_MSG_RESULT([configuring $PACKAGE_NAME $PACKAGE_VERSION])
AC_CANONICAL_TARGET([])
AM_INIT_AUTOMAKE([dist-bzip2 1.9 foreign])
AM_MAINTAINER_MODE
AC_CONFIG_HEADER([config.h])
AC_PREFIX_DEFAULT(/usr/local/Geomview)
GV_INIT_GEOMVIEW(=,1,>=,8)

AC_CONFIG_SRCDIR([src/transformer/transformer.main.c])

AC_PROG_INSTALL
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LIBTOOL

#
# Store X library link line in XLIBS
#
AC_PATH_XTRA
XLIBS="$X_LIBS $X_PRE_LIBS -lXt -lXext -lX11 $X_EXTRA_LIBS"
AC_SUBST(XLIBS)
AC_CACHE_VAL(ac_cv_XLIBS,[ac_cv_XLIBS="XLIBS='$XLIBS'"])

#
# Check for the xforms library
#
GEOMVIEW_CHECK_PACKAGE(Xpm, Xpm, ${x_libraries}, ${XLIBS},,,,optional,enabled)
GEOMVIEW_CHECK_PACKAGE(xforms, forms, ${x_libraries}, ${XLIBS} ${XPM_LIB} -lm, forms.h,,,optional,enabled)

# The stereo module needs to fiddle with monitor modes.
# Currently, this only works on IRIX using an external command.
#
AC_PATH_PROG([SETMON_PATH],[setmon],,[$PATH:/usr/gfx])
if test -n "$SETMON_PATH"; then
  AC_DEFINE_UNQUOTED([SETMON_PATH], "$SETMON_PATH", [Path to setmon program])
fi

########################################################################

AC_OUTPUT(Makefile
          src/Makefile
          src/cplxview/Makefile
          src/example/Makefile
          src/flythrough/Makefile
          src/ginsu/Makefile
          src/graffiti/Makefile
          src/hinge/Makefile
          src/stereo/Makefile
          src/sweep/Makefile
          src/tackdown/Makefile
          src/transformer/Makefile)