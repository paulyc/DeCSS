headers = css-auth.h
tstdvd_objs = tstdvd.o css-auth.o
validate_objs = validate.o css-auth.o
cat_objs = css-cat.o css-descramble.o

all: tstdvd resetdvd dvdinfo css-cat

install: all
	install -o root -g root -t /usr/local/bin tstdvd resetdvd dvdinfo css-cat
#	install -o root -g root -m 644 -t /usr/local/include css-auth.h css-descramble.h

tstdvd: $(tstdvd_objs) $(headers)
	gcc $(tstdvd_objs) -o $@

css-cat: $(cat_objs) css-descramble.h
	gcc $(cat_objs) -o $@

validate: $(validate_objs) $(headers)
	gcc $(validate_objs) -o $@

clean:
	-rm -f *.o tstdvd validate resetdvd dvdinfo css-cat

dist-files =	css-auth/COPYING css-auth/README css-auth/Makefile \
		css-auth/css-auth.h css-auth/css-auth.c \
		css-auth/tstdvd.c css-auth/dvdinfo.c css-auth/reset.c \
		css-auth/css-cat.c css-auth/css-descramble.c \
		css-auth/css-descramble.h

dist:
	(cd ..;tar cvf css-auth.tar $(dist-files) )
