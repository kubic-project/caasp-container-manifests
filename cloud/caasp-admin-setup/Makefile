DESTDIR=
ver = $(shell rpm -q --specfile --qf '%{NAME}-%{VERSION}\n' caasp-admin-setup.spec)
setup_ver = $(shell python ./setup.py --fullname)
ifneq ($(DESTDIR),)
DESTDIR_ARG=--root="$(DESTDIR)"
endif
ifneq ($(ver), $(setup_ver))
  $(error setup.py and caasp-admin-setup.spec versions differ)
endif

tar:
	mkdir -p "$(ver)/usr/sbin"
	cp license_MIT.txt "$(ver)/LICENSE"
	cp Makefile "$(ver)"
	cp -r caasp-admin-setup lib setup.py "$(ver)"
	tar -cjf "$(ver).tar.bz2" "$(ver)"
	rm -rf "$(ver)"

install:
	python setup.py $(DESTDIR_ARG)
