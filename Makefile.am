ACLOCAL_AMFLAGS = -I m4
DISTCHECK_CONFIGURE_FLAGS = --enable-gtk-doc --with-testdatadir=$(TESTDATADIR)

if BUILD_SPLASH_OUTPUT
splash_subdir = splash
splash_pc_file = poppler-splash.pc
endif

if BUILD_CAIRO_OUTPUT
cairo_pc_file = poppler-cairo.pc
endif

if BUILD_POPPLER_GLIB
glib_subdir = glib
glib_pc_file = poppler-glib.pc
endif

if BUILD_POPPLER_QT5
qt5_subdir = qt5
qt5_pc_file = poppler-qt5.pc
endif

if BUILD_POPPLER_QT4
qt4_subdir = qt4
qt4_pc_file = poppler-qt4.pc
endif


if BUILD_POPPLER_CPP
cpp_subdir = cpp
cpp_pc_file = poppler-cpp.pc
endif

SUBDIRS = goo fofi $(splash_subdir) poppler utils $(glib_subdir) test $(qt4_subdir) $(qt5_subdir) $(cpp_subdir)

EXTRA_DIST =					\
	README-XPDF				\
	poppler.pc.in				\
	poppler-uninstalled.pc.in		\
	poppler-cairo.pc.in			\
	poppler-cairo-uninstalled.pc.in		\
	poppler-splash.pc.in			\
	poppler-splash-uninstalled.pc.in	\
	poppler-qt4.pc.in			\
	poppler-qt4-uninstalled.pc.in		\
	poppler-qt5.pc.in			\
	poppler-qt5-uninstalled.pc.in		\
	poppler-cpp.pc.in			\
	poppler-cpp-uninstalled.pc.in

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA =				\
	poppler.pc				\
	$(cairo_pc_file)			\
	$(splash_pc_file)			\
	$(glib_pc_file)				\
	$(qt4_pc_file)				\
	$(qt5_pc_file)				\
	$(cpp_pc_file)

# Add CMake buildsystem files here so they get added on make dist
EXTRA_DIST +=							\
	cpp/tests/CMakeLists.txt				\
	cpp/CMakeLists.txt					\
	glib/demo/CMakeLists.txt				\
	glib/CMakeLists.txt					\
	glib/poppler-features.h.cmake				\
	qt4/src/CMakeLists.txt					\
	qt4/tests/CMakeLists.txt				\
	qt4/CMakeLists.txt					\
	qt4/demos/CMakeLists.txt				\
	qt5/src/CMakeLists.txt					\
	qt5/tests/CMakeLists.txt				\
	qt5/CMakeLists.txt					\
	qt5/demos/CMakeLists.txt				\
	test/CMakeLists.txt					\
	utils/CMakeLists.txt					\
	CMakeLists.txt						\
	ConfigureChecks.cmake					\
	cmake/modules/CheckFileOffsetBits.c			\
	cmake/modules/CheckFileOffsetBits.cmake			\
	cmake/modules/COPYING-CMAKE-SCRIPTS			\
	cmake/modules/FindCairo.cmake				\
	cmake/modules/FindFontconfig.cmake			\
	cmake/modules/FindGLIB.cmake				\
	cmake/modules/FindGObjectIntrospection.cmake		\
	cmake/modules/FindGTK.cmake				\
	cmake/modules/FindIconv.cmake				\
	cmake/modules/FindLCMS.cmake				\
	cmake/modules/FindLCMS2.cmake				\
        cmake/modules/FindNSS3.cmake				\
	cmake/modules/FindQt4.cmake				\
	cmake/modules/GObjectIntrospectionMacros.cmake		\
	cmake/modules/MacroBoolTo01.cmake			\
	cmake/modules/MacroEnsureVersion.cmake			\
	cmake/modules/MacroOptionalFindPackage.cmake		\
	cmake/modules/MacroPushRequiredVars.cmake		\
	cmake/modules/PopplerDefaults.cmake			\
	cmake/modules/PopplerMacros.cmake			\
	cmake/modules/FindLIBOPENJPEG.cmake			\
	cmake/modules/FindLIBOPENJPEG2.cmake			\
	config.h.cmake						\
	poppler-cairo.pc.cmake					\
	poppler/poppler-config.h.cmake				\
	poppler-cpp.pc.cmake					\
	poppler-glib.pc.cmake					\
	poppler-qt4.pc.cmake					\
	poppler-qt5.pc.cmake					\
	poppler-splash.pc.cmake					\
	poppler.pc.cmake



distclean-local:
	if test "$(srcdir)" = "."; then :; else \
		rm -f ChangeLog; \
	fi

ChangeLog:
	$(AM_V_GEN) if test -d "$(srcdir)/.git"; then \
	  (GIT_DIR=$(top_srcdir)/.git ./missing --run git log --stat) | fmt --split-only > $@.tmp \
	  && mv -f $@.tmp $@ \
	  || ($(RM) $@.tmp; \
	      echo Failed to generate ChangeLog, your ChangeLog may be outdated >&2; \
	      (test -f $@ || echo git log is required to generate this file >> $@)); \
	else \
	  test -f $@ || \
	  (echo A git checkout and git log is required to generate ChangeLog >&2 && \
	  echo A git checkout and git log is required to generate this file >> $@); \
	fi

.PHONY: ChangeLog

