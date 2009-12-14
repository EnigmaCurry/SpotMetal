# Build script for building on Ubuntu
# Needs openoffice.org-dev installed

PACKAGE_NAME = SpotMetal
OOO_HOME = /usr/lib/openoffice
OOO_BIN_DIR = $(OOO_HOME)/program
URE_BIN_DIR = /usr/lib/ure/bin
SDK_DIR = $(OOO_HOME)/basis3.1/sdk/
IDL_INCLUDE_DIR = $(SDK_DIR)/idl

all: clean package

package: idl/X$(PACKAGE_NAME).idl
	$(SDK_DIR)/bin/idlc -w -I "$(IDL_INCLUDE_DIR)" idl/X$(PACKAGE_NAME).idl
	$(URE_BIN_DIR)/regmerge idl/X$(PACKAGE_NAME).rdb /UCR idl/X$(PACKAGE_NAME).urd
	rm -f idl/X$(PACKAGE_NAME).urd
	mkdir -p $(PACKAGE_NAME)/META-INF
	python generate_xml.py
	mv manifest.xml $(PACKAGE_NAME)/META-INF
	mv description.xml $(PACKAGE_NAME)
	mv CalcAddIn.xcu $(PACKAGE_NAME)
	mv idl/X$(PACKAGE_NAME).rdb $(PACKAGE_NAME)
	cp src/*.py $(PACKAGE_NAME)
	cd $(PACKAGE_NAME); zip -r ../$(PACKAGE_NAME).oxt *

clean: 
	rm -rf $(PACKAGE_NAME)
	rm -f idl/X$(PACKAGE_NAME).urd
	rm -f idl/X$(PACKAGE_NAME).rdb
	rm -f $(PACKAGE_NAME).oxt

