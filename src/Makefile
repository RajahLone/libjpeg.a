
CROSSPREFIX=/opt/cross-mint/bin/m68k-atari-mint-
PATH = /opt/cross-mint/m68k-atari-mint/bin:/opt/cross-mint/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
LD_LIBRARY_PATH=/opt/cross-mint/lib:/opt/cross-mint/m68k-atari-mint/lib:$LD_LIBRARY_PATH
DESTDIR=/opt/cross-mint/m68k-atari-mint

CC = $(CROSSPREFIX)gcc
AS = $(CC)
AR = $(CROSSPREFIX)ar
RANLIB = $(CROSSPREFIX)ranlib
STRIP = $(CROSSPREFIX)strip
FLAGS = $(CROSSPREFIX)flags

CFLAGS = -I../include -I. -W

OFLAGS = -Wall -O2 -fomit-frame-pointer -Wno-unused-parameter

OBJS = jaricom.c jcapimin.c jcapistd.c jcarith.c jccoefct.c jccolor.c jcdctmgr.c jchuff.c \
       jcinit.c jcmainct.c jcmarker.c jcmaster.c jcomapi.c jcparam.c jcprepct.c jcsample.c \
       jctrans.c jdapimin.c jdapistd.c jdarith.c jdatadst.c jdatasrc.c jdcoefct.c jdcolor.c \
       jddctmgr.c jdhuff.c jdinput.c jdmainct.c jdmarker.c jdmaster.c jdmerge.c jdpostct.c \
       jdsample.c jdtrans.c jerror.c jfdctflt.c jfdctfst.c jfdctint.c jidctflt.c jidctfst.c \
       jidctint.c jquant1.c jquant2.c jutils.c jmemmgr.c jmemnobs.c

libjpeg.a:
	mkdir -p ../lib
	mkdir -p ../lib/m68020-60
	mkdir -p ../lib/m5475

	$(CC) $(CFLAGS) -m68000 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libjpeg.a $(DESTDIR)/lib/libjpeg.a
	cp libjpeg.a ../lib/libjpeg.a
	rm -f *.o libjpeg.a
	$(CC) $(CFLAGS) -m68020-60 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libjpeg.a $(DESTDIR)/lib/m68020-60/libjpeg.a
	cp libjpeg.a ../lib/m68020-60/libjpeg.a
	rm -f *.o libjpeg.a
	$(CC) $(CFLAGS) -mcpu=5475 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libjpeg.a $(DESTDIR)/lib/m5475/libjpeg.a
	cp libjpeg.a ../lib/m5475/libjpeg.a
	rm -f *.o libjpeg.a

clean:
	rm -f ../lib/libjpeg.a
	rm -f ../lib/m68020-60/libjpeg.a
	rm -f ../lib/m5475/libjpeg.a
	rm -f *.o libjpeg.a
