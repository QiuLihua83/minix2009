# Makefile for commands/i386.

CFLAGS	= -D_MINIX -D_POSIX_SOURCE
CCLD	= $(CC) -i $(CFLAGS)
MAKE	= exec make -$(MAKEFLAGS)
CC = exec cc

all::	acd

acd:	acd.c
	$(CCLD) -o $@ -DARCH=\"`arch`\" -DDESCR=\"/usr/lib/descr\" $?
	install -S 50kw $@

install::	/usr/bin/acd /usr/bin/cc /usr/bin/m2 /usr/bin/pc \
		/usr/lib/descr

/usr/bin/acd:	acd
	install -cs -o bin $? $@

/usr/bin/cc /usr/bin/m2 /usr/bin/pc:	/usr/bin/acd
	install -l $? $@

/usr/lib/descr:	acd.descr
	install $? $@

clean::
	rm -rf a.out core acd

all install clean::
	cd asmconv && $(MAKE) $@
