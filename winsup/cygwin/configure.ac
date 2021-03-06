dnl Autoconf configure script for Cygwin.
dnl
dnl This file is part of Cygwin.
dnl
dnl This software is a copyrighted work licensed under the terms of the
dnl Cygwin license.  Please consult the file "CYGWIN_LICENSE" for
dnl details.
dnl
dnl Process this file with autoconf to produce a configure script.

AC_PREREQ([2.59])
AC_INIT([Cygwin DLL],[0],[cygwin@cygwin.com],[cygwin],[https://cygwin.com])
AC_CONFIG_SRCDIR(Makefile.in)
AC_CONFIG_HEADER(config.h)
AC_CONFIG_AUX_DIR(..)

. ${srcdir}/../configure.cygwin

AC_PROG_INSTALL
AC_NO_EXECUTABLES
AC_CANONICAL_TARGET

AC_PROG_CC
AC_PROG_CXX
AC_PROG_CPP
AC_LANG(C)

AC_LANG(C++)

AC_CYGWIN_INCLUDES

AC_CHECK_TOOL(AR, ar, ar)
AC_CHECK_TOOL(AS, as, as)
AC_CHECK_TOOL(DLLTOOL, dlltool, dlltool)
AC_CHECK_TOOL(LD, ld, ld)
AC_CHECK_TOOL(NM, nm, nm)
AC_CHECK_TOOL(OBJCOPY, objcopy, objcopy)
AC_CHECK_TOOL(OBJDUMP, objdump, objdump)
AC_CHECK_TOOL(RANLIB, ranlib, ranlib)
AC_CHECK_TOOL(STRIP, strip, strip)
AC_CHECK_TOOL(WINDRES, windres, windres)

AC_ARG_ENABLE(debugging,
[ --enable-debugging		Build a cygwin DLL which has more consistency checking for debugging],
[case "${enableval}" in
yes)	 AC_DEFINE([DEBUGGING],[1],[Define if DEBUGGING support is requested.]) ;;
no)	 ;;
esac
])

case "$target_cpu" in
   i?86)
		DLL_ENTRY="_dll_entry@12"
		DEF_DLL_ENTRY="dll_entry@12"
		DIN_FILE="i686.din"
		TLSOFFSETS_H="tlsoffsets.h"
		;;
   x86_64)
		DLL_ENTRY="dll_entry"
		DEF_DLL_ENTRY="dll_entry"
		DIN_FILE="x86_64.din"
		TLSOFFSETS_H="tlsoffsets64.h"
		;;
   *)		AC_MSG_ERROR([Invalid target processor "$target_cpu"]) ;;
esac

AC_CONFIGURE_ARGS
AC_SUBST(DLL_ENTRY)
AC_SUBST(DEF_DLL_ENTRY)
AC_SUBST(DIN_FILE)
AC_SUBST(TLSOFFSETS_H)
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
