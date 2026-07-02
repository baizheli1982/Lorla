include ../../Makefile.include
PLATFORM=$(NATIVEPLATFORM)
DEPS = ../../Makefile.include Makefile

APPNAME=cmake
VERSION=3.26.4

APP=$(PLATFORM)/bin/$(APPNAME)

all: .installed-$(PLATFORM)

$(PLATFORM):
	mkdir -p $(PLATFORM)/bin $(PLATFORM)/share

$(APP): $(PLATFORM)
	ln -sf $(shell which cmake) $(PLATFORM)/bin/cmake
	ln -sf $(shell which ctest) $(PLATFORM)/bin/ctest 2>/dev/null || true
	ln -sf $(shell which cpack) $(PLATFORM)/bin/cpack 2>/dev/null || true
	touch $@

.installed-$(PLATFORM): $(APP)
	mkdir -p $(NATIVEPREFIX)/bin
	ln -sf $(shell which cmake) $(NATIVEPREFIX)/bin/cmake
	ln -sf $(shell which ctest) $(NATIVEPREFIX)/bin/ctest 2>/dev/null || true
	ln -sf $(shell which cpack) $(NATIVEPREFIX)/bin/cpack 2>/dev/null || true
	touch $@

clean:
	rm -f .installed-$(PLATFORM) $(APP)

distclean::
	rm -rf $(PLATFORM) .installed-$(PLATFORM)
