# A sample Makefile for building both Google Mock and Google Test and
# using them in user tests.  This file is self-contained, so you don't
# need to use the Makefile in Google Test's source tree.  Please tweak
# it to suit your environment and project.  You may want to move it to
# your project's root directory.
#
# SYNOPSIS:
#
#   make [all]  - makes everything.
#   make TARGET - makes the given target.
#   make clean  - removes all files generated by make.

# Please tweak the following variable definitions as needed by your
# project, except GMOCK_HEADERS and GTEST_HEADERS, which you can use
# in your own targets but shouldn't modify.

# Points to the root of Google Test, relative to where this file is.
# Remember to tweak this if you move this file, or if you want to use
# a copy of Google Test at a different location.
GTEST_DIR = /home/bart/git/googletest/googletest

# Points to the root of Google Mock, relative to where this file is.
# Remember to tweak this if you move this file.
GMOCK_DIR = /home/bart/git/googletest/googlemock

# Where to find user code.
USER_DIR = ./

# Flags passed to the preprocessor.
# Set Google Test and Google Mock's header directories as system
# directories, such that the compiler doesn't generate warnings in
# these headers.
CPPFLAGS += -isystem $(GTEST_DIR)/include -isystem $(GMOCK_DIR)/include

# Flags passed to the C++ compiler.
CXXFLAGS += -g -Wall -Wextra -pthread

# Include flags
INCLUDE += -I$(GTEST_DIR)/include -I$(GMOCK_DIR)/include
CPPFLAGS += $(INCLUDE)

# Linker libs
LDFLAGS += -L$(GTEST_DIR) -L$(GMOCK_DIR)
LDFLAGS += -lgtest -lgmock -lpthread

# All tests produced by this Makefile.  Remember to add new tests you
# created to the list.
TEST_SRC = \
        test_all.cpp

TEST_OBJ = $(TEST_SRC:.cpp=.o)

# House-keeping build targets.

all : runtests $(TEST_OBJ)
	@echo $(TEST_OBJ)

clean :
	rm -f $(TEST_OBJ) *.o

# Builds a sample test.

%.o : %.cpp
	@$(CXX) $(CPPFLAGS) $(CXXFLAGS) -c $(USER_DIR)/$<

runtests: $(TEST_OBJ)
	@$(CXX) $(CPPFLAGS) $(CXXFLAGS) $^ -o $@ $(LDFLAGS)
