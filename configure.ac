#  Copyright 2016 Intel Corporation
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
AC_PREREQ([2.68])

m4_pattern_allow([AC_CONFIG_MACRO])
## it is interface version for libtool, only change it if you are sure to do so
m4_define([libyamiutils_lt_current], 0)
m4_define([libyamiutils_lt_revision], 1)
m4_define([libyamiutils_lt_age], 0)
m4_define([libyamiutils_lt_version], [libyamiutils_lt_current.libyamiutils_lt_revision.libyamiutils_lt_age])

# package version (lib name suffix), usually sync with git tag
m4_define([libyamiutils_major_version], 0)
m4_define([libyamiutils_minor_version], 1)
# even number of micro_version means a release after full validation cycle
m4_define([libyamiutils_micro_version], 0)
m4_define([libyamiutils_version],
                    [libyamiutils_major_version.libyamiutils_minor_version.libyamiutils_micro_version])

AC_INIT([libyamiutils],
        [libyamiutils_version],
        [https://github.com/01org/libyami-utils/issues/new],
        [libyamiutils],
        [https://github.com/01org/libyami-utils])

AC_CONFIG_SRCDIR([tests/decodeinput.h])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])
AM_INIT_AUTOMAKE([foreign subdir-objects])
AM_SILENT_RULES([yes])

LIBYAMIUTILS_LT_VERSION="libyamiutils_major_version:libyamiutils_minor_version:libyamiutils_micro_version"
LIBYAMIUTILS_LT_LDFLAGS="-version-number $LIBYAMIUTILS_LT_VERSION"
AC_SUBST(LIBYAMIUTILS_LT_VERSION)
AC_SUBST(LIBYAMIUTILS_LT_LDFLAGS)

AC_ARG_ENABLE(tests-gles,
    [AC_HELP_STRING([--enable-tests-gles],
        [build with extra gles tests @<:@default=no@:>@])],
    [], [enable_test_gles="no"])

if test "$enable_tests_gles" = "yes"; then
    AC_DEFINE([__ENABLE_TESTS_GLES__], [1],
        [Defined to 1 if --enable-tests-gles="yes"])
fi

AM_CONDITIONAL(ENABLE_TESTS_GLES,
    [test "x$enable_tests_gles" = "xyes"])

AC_ARG_ENABLE(debug,
    [AC_HELP_STRING([--enable-debug],
        [build with extra debug @<:@default=no@:>@])],
    [], [enable_debug="no"])

if test "$enable_debug" = "yes"; then
    AC_DEFINE([__ENABLE_DEBUG__], [1],
        [Defined to 1 if --enable-debug="yes"])
fi

GTEST_LIB_CHECK([1.7.0], [:], [:])
AM_CONDITIONAL([ENABLE_UNITTESTS],
[test "x$HAVE_GTEST" = "xyes"])

AC_ARG_ENABLE(dmabuf,
    [AC_HELP_STRING([--enable-dmabuf],
        [support dma_buf buffer sharing @<:@default=no@:>@])],
    [], [enable_dmabuf="no"])

if test "$enable_dmabuf" = "yes"; then
    AC_DEFINE([__ENABLE_DMABUF__], [1],
        [Defined to 1 if --enable-dmabuf="yes"])
fi
AM_CONDITIONAL(ENABLE_DMABUF,
    [test "x$enable_dmabuf" = "xyes"])

AC_ARG_ENABLE(v4l2,
    [AC_HELP_STRING([--enable-v4l2],
        [wrapper of v4l2 interface @<:@default=no@:>@])],
    [], [enable_v4l2="no"])

AC_ARG_ENABLE(v4l2-glx,
    [AC_HELP_STRING([--enable-v4l2-glx],
        [use glx/tfp in v4l2 wrapper @<:@default=no@:>@])],
    [], [enable_v4l2_glx="no"])

if test "$enable_v4l2" = "yes"; then
    AC_DEFINE([__ENABLE_V4L2__], [1],
        [Defined to 1 if --enable-v4l2="yes"])
fi
AM_CONDITIONAL(ENABLE_V4L2,
    [test "x$enable_v4l2" = "xyes"])

AC_ARG_ENABLE(capi,
    [AC_HELP_STRING([--enable-capi],
        [wrapper of c api interface @<:@default=no@:>@])],
    [], [enable_capi="no"])

if test "$enable_capi" = "yes"; then
    AC_DEFINE([__ENABLE_CAPI__], [1],
        [Defined to 1 if --enable-capi="yes"])
fi
AM_CONDITIONAL(ENABLE_CAPI,
    [test "x$enable_capi" = "xyes"])

AC_ARG_ENABLE(x11,
    [AC_HELP_STRING([--enable-x11],
        [enable x11 @<:@default=yes@:>@])],
    [], [enable_x11="yes"])

if test "$enable_x11" = "yes"; then
    AC_DEFINE([__ENABLE_X11__], [1],
        [Defined to 1 if --enable-x11="yes"])
fi
AM_CONDITIONAL(ENABLE_X11,
    [test "x$enable_x11" = "xyes"])

AC_ARG_ENABLE(avformat,
    [AC_HELP_STRING([--enable-avformat],
        [enable avformat @<:@default=no@:>@])],
    [], [enable_avformat="no"])

if test "$enable_avformat" = "yes"; then
    AC_DEFINE([__ENABLE_AVFORMAT__], [1],
        [Defined to 1 if --enable-avformat="yes"])
fi
AM_CONDITIONAL(ENABLE_AVFORMAT,
    [test "x$enable_avformat" = "xyes"])

AC_ARG_ENABLE(md5,
    [AC_HELP_STRING([--enable-md5], [enable generate md5 by per frame@<:@default=yes@:>@])],
    [], [enable_md5="yes"])

dnl encoder getmv
AC_ARG_ENABLE(getmv,
    [AC_HELP_STRING([--enable-getmv],
        [build with get mv support @<:@default=no@:>@])],
    [], [enable_getmv="no"])

if test "$enable_getmv" = "yes"; then
    AC_DEFINE([__BUILD_GET_MV__], [1],
        [Defined to 1 if --enable-getmv="yes"])
fi
AM_CONDITIONAL(BUILD_GET_MV,
    [test "x$enable_getmv" = "xyes"])

dnl ocl blender
AC_ARG_ENABLE(oclblender,
    [AC_HELP_STRING([--enable-oclblender],
        [build with opencl based alpha blend support @<:@default=no@:>@])],
    [], [enable_oclblender="no"])

AM_CONDITIONAL(BUILD_OCL_BLENDER,
    [test "x$enable_oclblender" = "xyes"])



dnl : ${CFLAGS="-g -O2 -Wno-unused-function -Wno-sign-compare -Wno-cpp -Wall -Werror"}
dnl : ${CXXFLAGS="-g -O2 -Wno-unused-function -Wno-sign-compare -Wno-cpp -Wall -Werror"}

# Checks for programs.
AC_DISABLE_STATIC
AC_PROG_CXX
AC_PROG_AWK
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET
AC_PROG_LIBTOOL
#LT_INIT
# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([stddef.h stdint.h stdlib.h string.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_SIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

pkgconfigdir=${libdir}/pkgconfig
AC_SUBST(pkgconfigdir)

# Check for libva (vaapi version)
PKG_CHECK_MODULES([LIBVA], [libva])
AC_SUBST(LIBVA_VERSION)

PKG_CHECK_MODULES([LIBVA_DRM], [libva-drm])

if test "$enable_x11" = "yes"; then
    PKG_CHECK_MODULES([LIBVA_X11], [libva-x11],
        [AC_DEFINE([HAVE_VA_X11], [1],
            [Defined to 1 if VA/X11 API is enabled])],
        [])
    PKG_CHECK_MODULES([X11], [x11])
fi

if test "$enable_v4l2" = "yes"; then
    PKG_CHECK_MODULES([LIBV4L2], [libv4l2])
    PKG_CHECK_MODULES([LIBYAMIV4L2], [libyami_v4l2])
fi

if test "$enable_tests_gles" = "yes"; then
    PKG_CHECK_MODULES([LIBEGL], [egl])
    PKG_CHECK_MODULES([LIBGLES2], [glesv2])
fi

dnl drm_fourcc.h for dma_buf support
if test "$enable_dmabuf" = "yes"; then
    PKG_CHECK_MODULES([LIBDRM], [libdrm])
fi

if test "$enable_avformat" = "yes"; then
    PKG_CHECK_MODULES(LIBAVFORMAT,  [libavformat libavcodec libavutil])
fi

#check openssl
if test "$enable_md5" = "yes"; then
    PKG_CHECK_MODULES([LIBBSD], [libbsd],
        [AC_DEFINE([__ENABLE_MD5__], [1],
            [Defined to 1 if MD5 API and --enable-md5[default] are enabled])],
        [])
fi

PKG_CHECK_MODULES([LIBYAMI], [libyami])

AM_CONDITIONAL(ENABLE_MD5, test "x$enable_md5" = "xyes")

# Checks for library functions.
AC_FUNC_MALLOC
AC_FUNC_REALLOC
AC_CHECK_FUNCS([memset strcasecmp strdup])

AC_CONFIG_FILES([Makefile
                 tests/Makefile
		 examples/Makefile
		 testscripts/Makefile])

AC_OUTPUT

# Print a configuration summary
APPS="yamidecode yamiencode yamiinfo yamitranscode yamivpp"

AS_IF([test x$enable_v4l2 = xyes], [APPS="$APPS v4l2decode v4l2encode"])
AS_IF([test x$enable_capi = xyes], [APPS="$APPS decodecapi encodecapi"])


AC_MSG_RESULT([
    libyami - libyamiutils_version

    Build utils ...................... : $APPS
    Build gtest unit tests ........... : $HAVE_GTEST
    Enable debug ..................... : $enable_debug
    Installation prefix .............. : $prefix
])
