#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.61])
AC_INIT([manpages-zh],[1.5.2],[https://github.com/lidaobing/manpages-zh/issues])
AM_INIT_AUTOMAKE([dist-bzip2 subdir-objects])
AM_MAINTAINER_MODE

AC_ARG_ENABLE([utf8],
              [AS_HELP_STRING([--disable-utf8],
                              [don't generate manpages in utf8 encoding,
                               use gbk and big5 encoding])],
              [case "${enableval}" in
                       yes) utf8=true ;;
                no) utf8=false ;;
                *) AC_MSG_ERROR([bad value ${enableval} for --enable-utf8]) ;;
                esac],
              [utf8=true])
AM_CONDITIONAL([UTF8], [test x$utf8 = xtrue])

AC_ARG_ENABLE([zhtw],
              [AS_HELP_STRING([--disable-zhtw],
                              [do not generate manpages for zh_TW])],
              [case "${enableval}" in
                       yes) zhtw=true ;;
                no) zhtw=false ;;
                *) AC_MSG_ERROR([bad value ${enableval} for --enable-zhtw]) ;;
                esac],
              [zhtw=true]
              )
if test x$zhtw = xtrue; then
AC_PATH_PROG([AUTOB5], [autob5])
if test x$AUTOB5 = x; then
        AC_MSG_ERROR([cannot find autob5, you can install zh-autoconvert from http://ftp.debian.org/debian/pool/main/z/zh-autoconvert, or use --disable-zhtw])
fi
AC_PATH_PROG([ICONV], [iconv])
if test x$ICONV = x; then
        AC_MSG_ERROR([cannot find iconv, you can use --disable-zhtw])
fi
AC_PATH_PROG([PERL], [perl])
if test x$PERL = x; then
        AC_MSG_ERROR([cannot find perl, you can use --disable-zhtw])
fi
zh_TW=zh_TW
AC_SUBST(zh_TW)
fi

AC_ARG_ENABLE([zhcn],
              [AS_HELP_STRING([--disable-zhcn],
                              [do not generate manpage for zh_CN])],
              [case "${enableval}" in
                yes) zhcn=true ;;
                no) zhcn=false ;;
                *) AC_MSG_ERROR([bad value ${enableval} for --enable-zhcn]) ;;
                esac],
              [zhcn=true]
              )
if test x$zhcn = xtrue; then
        zh_CN=zh_CN
        AC_SUBST(zh_CN)
fi

AC_ARG_ENABLE([cjkpunct-workaround],
              [AS_HELP_STRING([--enable-cjkpunct-workaround],
                              [install cjkpunct workaround for groff << 1.22.4])],
              [case "${enableval}" in
                yes) enable_cjkpunct_workaround=true ;;
                no) enable_cjkpunct_workaround=false ;;
                *) AC_MSG_ERROR([bad value ${enableval} for --enable-cjkpunct-workaround]) ;;
               esac],
              [enable_cjkpunct_workaround=false]
              )
AM_CONDITIONAL(CJKPUNCT_WORKAROUND, [test x"${enable_cjkpunct_workaround}" = x"true" ])

AC_CONFIG_FILES([Makefile
                 DOCS/Makefile
                 src/Makefile
                 src/man1/Makefile
                 src/man1/zh_CN/Makefile
                 src/man1/zh_TW/Makefile
                 src/man2/Makefile
                 src/man2/zh_CN/Makefile
                 src/man2/zh_TW/Makefile
                 src/man3/Makefile
                 src/man3/zh_CN/Makefile
                 src/man3/zh_TW/Makefile
                 src/man4/Makefile
                 src/man4/zh_CN/Makefile
                 src/man4/zh_TW/Makefile
                 src/man5/Makefile
                 src/man5/zh_CN/Makefile
                 src/man5/zh_TW/Makefile
                 src/man6/Makefile
                 src/man6/zh_CN/Makefile
                 src/man6/zh_TW/Makefile
                 src/man7/Makefile
                 src/man7/zh_CN/Makefile
                 src/man7/zh_TW/Makefile
                 src/man8/Makefile
                 src/man8/zh_CN/Makefile
                 src/man8/zh_TW/Makefile
                 src/mann/Makefile
                 src/mann/zh_CN/Makefile
                 src/mann/zh_TW/Makefile
                 utils/Makefile
                 ])
AC_OUTPUT

echo
echo "manpages-zh configure summary"
echo "============================="
echo "UTF-8 : $utf8"
echo "zh_CN : $zhcn"
echo "zh_TW : $zhtw"
echo
