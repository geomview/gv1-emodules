AC_PREREQ(2.59)
AC_INIT(gvemod-ndview,
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

AC_CONFIG_SRCDIR([src/NDview/ndview.c])

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

# Cygwin does not seem to have the Tcl_CreateFileHandler() function,
# so test for it.
if test -n "${TCL_LIB}" -a -n "${TK_LIB}"; then
    ac_save_LIBS="${LIBS}"
    LIBS="${TCL_ALL_LIB} ${LIBS}"
    AC_CHECK_FUNCS([Tcl_CreateFileHandler],
	[TCLFILEHANDLER=yes],
	[TCLFILEHANDLER=no])
    LIBS="${ac_save_LIBS}"
fi
AM_CONDITIONAL([TCLFILEHANDLER], [test "z${TCLFILEHANDLER}" = "zyes"])

################################################################################

AC_OUTPUT(Makefile
          src/Makefile
          src/NDview/Makefile
          src/ndutils/Makefile)
