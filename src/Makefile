SHELL := /bin/bash

HDF_ROOT = /usr

OPT_FLAG = -O0
CXXFLAGS = -Wall -Wextra -pedantic -g3 -ggdb -fno-eliminate-unused-debug-types ${OPT_FLAG}
M_CXXFLAGS = -std=c++11 -pthread
CPPFLAGS = -isystem ${HDF_ROOT}/include -I fast5/src -I tclap/include -I hpptools/include

TARGETS = compute-state-transitions compute-scaled-pore-model run-fwbw run-viterbi nanocall

.PHONY: all test clean

all: ${TARGETS}

clean:
	rm -rf ${TARGETS}

compute-state-transitions: compute-state-transitions.cpp
	${CXX} ${M_CXXFLAGS} ${CXXFLAGS} ${CPPFLAGS} $^ -o $@ ${LDFLAGS}

compute-scaled-pore-model: compute-scaled-pore-model.cpp
	${CXX} ${M_CXXFLAGS} ${CXXFLAGS} ${CPPFLAGS} $^ -o $@ ${LDFLAGS} -L ${HDF_ROOT}/lib -lhdf5

run-fwbw: run-fwbw.cpp
	${CXX} ${M_CXXFLAGS} ${CXXFLAGS} ${CPPFLAGS} $^ -o $@ ${LDFLAGS} -lz

run-viterbi: run-viterbi.cpp
	${CXX} ${M_CXXFLAGS} ${CXXFLAGS} ${CPPFLAGS} $^ -o $@ ${LDFLAGS} -lz

nanocall: nanocall.cpp Builtin_Model.cpp
	${CXX} ${M_CXXFLAGS} ${CXXFLAGS} ${CPPFLAGS} $^ -o $@ ${LDFLAGS} -L ${HDF_ROOT}/lib -lhdf5 -lz

list-directory: list-directory.cpp
	${CXX} ${M_CXXFLAGS} ${CXXFLAGS} ${CPPFLAGS} $^ -o $@ ${LDFLAGS}
