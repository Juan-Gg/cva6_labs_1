#
# File: Makefile
# Description: Makefile for running the victim cache testbench.
#
CORE_FILE = victim_cache.core
VENDOR	= ucsbece154b
LIBRARY	= caching
CORE	= victim_cache
VERSION	= 1.0.0
PROJECT = ${VENDOR}:${LIBRARY}:${CORE}:${VERSION}

TESTS = $(shell find tests -type f)

# ======================================================= #

.PHONY: init build sim lint_1way lint_2way lint_4way lint_16way synth clean

# ======================================================= #
# Targets

sim: fusesoc.conf
	fusesoc run --target tb --tool ${TOOL} ${PROJECT}

init: fusesoc.conf

lint_1way: fusesoc.conf
	fusesoc run --target $@ ${PROJECT}
lint_2way: fusesoc.conf
	fusesoc run --target $@ ${PROJECT}
lint_4way: fusesoc.conf
	fusesoc run --target $@ ${PROJECT}
lint_16way: fusesoc.conf
	fusesoc run --target $@ ${PROJECT}

synth:
	cd synth && make

clean:
	rm -rf build fusesoc.conf

# ======================================================= #
# Files

fusesoc.conf:
	pip3 install --user -r requirements.txt
	rm -f fusesoc.conf
	fusesoc library add ${VENDOR}_${LIBRARY}_${CORE}_${VERSION} . --sync-type=local

# ======================================================= #
