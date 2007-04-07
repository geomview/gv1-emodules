AC_INIT(gvemod-xforms-example, [0.1], Claus-Justus Heine <Claus.Heine@Mathematik.Uni-Freiburg.DE>)

AC_CONFIG_SRCDIR([src/main.c])

GV_INIT_GEOMVIEW(=,1,>=,9)

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
GEOMVIEW_CHECK_PACKAGE(Xpm, Xpm, ${x_libraries}, ${XLIBS},[],[],[],[optional enabled])
if test -n "${x_includes}"; then
  ac_gv_xheaders="-I${x_includes} -I${x_includes}/X11"
fi
GEOMVIEW_CHECK_PACKAGE(xforms, forms, ${x_libraries}, ${XLIBS} ${XPM_LIB} -lm, forms.h,[],[${ac_gv_xheaders}],[required enabled])

########################################################################

GEOMVIEW_RESULT

AC_OUTPUT(Makefile src/Makefile)
