all: main-static main-dynamic

mean.o : mean.c
	gcc -fPIC -c mean.c

lib/libmean.a : mean.o
	[ -d lib ] || mkdir lib
	ar rcs lib/libmean.a mean.o

lib/libmean.so : mean.o
	[ -d lib ] || mkdir lib
	gcc -shared -o lib/libmean.so  mean.o

main-static : main.c lib/libmean.a
	gcc main.c -static -o main-static -L lib -lmean

main-dynamic : main.c lib/libmean.so
	gcc main.c -o main-dynamic -L lib -lmean

clean:
	rm -rf lib *.o main-static main-dynamic

