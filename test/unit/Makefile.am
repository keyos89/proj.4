AUTOMAKE_OPTIONS = subdir-objects

EXTRA_DIST = CMakeLists.txt

noinst_HEADERS = gtest_include.h

AM_CPPFLAGS = -I$(top_srcdir)/src -I$(top_srcdir)/include -I$(top_srcdir)/test -I$(top_srcdir)/test/googletest/include @SQLITE3_FLAGS@
AM_CXXFLAGS = @CXX_WFLAGS@ @NO_ZERO_AS_NULL_POINTER_CONSTANT_FLAG@

PROJ_LIB ?= ../../data

noinst_PROGRAMS = pj_transform_test
noinst_PROGRAMS += pj_phi2_test
noinst_PROGRAMS += proj_errno_string_test
noinst_PROGRAMS += proj_angular_io_test
noinst_PROGRAMS += proj_context_test
noinst_PROGRAMS += test_cpp_api
noinst_PROGRAMS += gie_self_tests
noinst_PROGRAMS += include_proj_h_from_c

pj_transform_test_SOURCES = pj_transform_test.cpp main.cpp
pj_transform_test_LDADD = ../../src/libproj.la ../../test/googletest/libgtest.la

pj_transform_test-check: pj_transform_test
	PROJ_LIB=$(PROJ_LIB) ./pj_transform_test

pj_phi2_test_SOURCES = pj_phi2_test.cpp main.cpp
pj_phi2_test_LDADD = ../../src/libproj.la ../../test/googletest/libgtest.la

pj_phi2_test-check: pj_phi2_test
	./pj_phi2_test

proj_errno_string_test_SOURCES = proj_errno_string_test.cpp main.cpp
proj_errno_string_test_LDADD= ../../src/libproj.la ../../test/googletest/libgtest.la

proj_errno_string_test-check: proj_errno_string_test
	./proj_errno_string_test

proj_angular_io_test_SOURCES = proj_angular_io_test.cpp main.cpp
proj_angular_io_test_LDADD = ../../src/libproj.la ../../test/googletest/libgtest.la

proj_angular_io_test-check: proj_angular_io_test
	./proj_angular_io_test

proj_context_test_SOURCES = proj_context_test.cpp main.cpp
proj_context_test_LDADD = ../../src/libproj.la ../../test/googletest/libgtest.la

proj_context_test-check: proj_context_test
	./proj_context_test

test_cpp_api_SOURCES = test_util.cpp test_common.cpp test_crs.cpp test_metadata.cpp test_io.cpp test_operation.cpp test_datum.cpp test_factory.cpp test_c_api.cpp main.cpp
test_cpp_api_LDADD = ../../src/libproj.la ../../test/googletest/libgtest.la @SQLITE3_LDFLAGS@

test_cpp_api-check: test_cpp_api
	PROJ_LIB=$(PROJ_LIB) ./test_cpp_api

gie_self_tests_SOURCES = gie_self_tests.cpp main.cpp
gie_self_tests_LDADD = ../../src/libproj.la ../../test/googletest/libgtest.la @SQLITE3_LDFLAGS@

gie_self_tests-check: gie_self_tests
	PROJ_LIB=$(PROJ_LIB) ./gie_self_tests

include_proj_h_from_c_SOURCES = include_proj_h_from_c.c

check-local: pj_transform_test-check pj_phi2_test-check proj_errno_string_test-check proj_angular_io_test-check proj_context_test-check test_cpp_api-check gie_self_tests-check
