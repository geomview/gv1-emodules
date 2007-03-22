AC_PREREQ(2.59)
AC_INIT(gvemodules-tcltk,
        [0.1], Claus-Justus Heine <Claus.Heine@Mathematik.Uni-Freiburg.DE>)
AC_MSG_RESULT([configuring $PACKAGE_NAME $PACKAGE_VERSION])
AC_CANONICAL_TARGET([])
AM_INIT_AUTOMAKE([dist-bzip2 foreign 1.9])
AM_MAINTAINER_MODE
AC_CONFIG_HEADER([config.h])
AC_PREFIX_DEFAULT(/usr/local/Geomview)
GV_INIT_GEOMVIEW(=,1,>=,8)
AC_PROG_INSTALL
GV_INIT_GEOMVIEW

AC_CONFIG_SRCDIR([src/crayola/tkcrayola.c])

################################################################################
#
# emodule specific checks.
#

# Check for Tcl/Tk with new CHECK_PACKAGE macro:

GEOMVIEW_CHECK_PACKAGE(tcl, tcl, ${x_libraries}, ${XLIBS}, tcl.h, , ,required)
if test -n "${TCL_LIB}"; then
  GEOMVIEW_CHECK_PACKAGE(tk, tk, ${x_libraries}, ${XLIBS}, tk.h, , ,required)
else
  AM_CONDITIONAL(HAVE_TK, [false])
fi
AM_CONDITIONAL(HAVE_TCLTK, [test -n "${TCL_LIB}" -a -n "${TK_LIB}"])

################################################################################

AC_OUTPUT(Makefile
          src/Makefile
          src/crayola/Makefile
          src/labeler/Makefile)
