AC_INIT(gvemod-labeler,
        [0.1], Claus-Justus Heine <Claus.Heine@Mathematik.Uni-Freiburg.DE>)

AC_CONFIG_SRCDIR([src/labeler.c])

GV_INIT_GEOMVIEW(=,1,>=,9)

################################################################################
#
# emodule specific checks.
#

#
# Store X library link line in XLIBS
#
AC_PATH_XTRA
XLIBS="$X_LIBS $X_PRE_LIBS -lXt -lXext -lX11 $X_EXTRA_LIBS"
AC_SUBST(XLIBS)
AC_CACHE_VAL(ac_cv_XLIBS,[ac_cv_XLIBS="XLIBS='$XLIBS'"])

# Check for Tcl/Tk with new CHECK_PACKAGE macro:

GEOMVIEW_CHECK_PACKAGE(tcl, tcl, ${x_libraries}, ${XLIBS}, tcl.h, , ,required)
if test -n "${TCL_LIB}"; then
  GEOMVIEW_CHECK_PACKAGE(tk, tk, ${x_libraries}, ${XLIBS}, tk.h, , ,required)
else
  AM_CONDITIONAL(HAVE_TK, [false])
fi
AM_CONDITIONAL(HAVE_TCLTK, [test -n "${TCL_LIB}" -a -n "${TK_LIB}"])

# Cygwin does not seem to have the Tcl_CreateFileHandler() function,
# so test for it and disable the crayola module in this case.
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

AC_OUTPUT(Makefile src/Makefile)
