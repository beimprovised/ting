include ../../platform.mk

binary_name := tests

ifeq ($(platform),windows)
binary_name := $(binary_name).exe
endif

default: $(binary_name)

ifeq ($(platform),windows)
    libs :=
endif
ifeq ($(platform),macosx)
    libs :=
endif
ifeq ($(platform),linux)
    libs := -pthread
endif


#external compiler flags (to be passed to make from command line)
ecf :=

#compiler flags
cf := $(ecf)
cf += -Wall
cf += -DDEBUG
cf += -fstrict-aliasing #strict aliasing!!!

compiler := g++
ifeq ($(platform),macosx)
    compiler := clang++
endif


include ../test_target.mk

include ../libting.mk

$(binary_name): main.cpp tests.cpp $(libting)
	@echo Building $@...
	@$(compiler) -o $@ $(cf) $^ $(libs)



clean:
	@rm -rf $(binary_name)

include ../../targets.mk

