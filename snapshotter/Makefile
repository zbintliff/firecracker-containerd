# Copyright 2018-2019 Amazon.com, Inc. or its affiliates. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License"). You may
# not use this file except in compliance with the License. A copy of the
# License is located at
#
# 	http://aws.amazon.com/apache2.0/
#
# or in the "license" file accompanying this file. This file is distributed
# on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either
# express or implied. See the License for the specific language governing
# permissions and limitations under the License.

# Set this to pass additional commandline flags to the go compiler, e.g. "make test EXTRAGOARGS=-v"
EXTRAGOARGS:=

SUBDIRS:=cmd/devmapper cmd/naive
SOURCES:=$(shell find . -name '*.go')
GOMOD := $(shell go env GOMOD)
GOSUM := $(GOMOD:.mod=.sum)

all: $(SUBDIRS)

$(SUBDIRS):
	$(MAKE) -C $@

install: $(SUBDIRS)
	for d in $(SUBDIRS); do $(MAKE) -C $$d install; done

test: $(SOURCES) $(GOMOD) $(GOSUM)
	go test ./... $(EXTRAGOARGS)

clean:
	for d in $(SUBDIRS); do $(MAKE) -C $$d clean; done

.PHONY: all $(SUBDIRS) clean install test
