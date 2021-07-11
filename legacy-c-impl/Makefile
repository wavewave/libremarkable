CFLAGS ?= -fPIC -g -static

all: poc spy.so evtest

libremarkable/%:
	make -C libremarkable

evtest:
	$(CC) $(CFLAGS) evtest.c -o evtest

poc: libremarkable/libremarkable.a
	$(CXX) $(CFLAGS) -c poc.cc -o poc.o
	$(CXX) $(CFLAGS) poc.o libremarkable/libremarkable.a -lfreetype -o poc

spy.so: libremarkable/libremarkable.a
	$(CC) $(CFLAGS) -c spy.c -o spy.o
	$(CC) $(CFLAGS) -shared spy.o libremarkable/libremarkable.a -ldl -o spy.so

clean:
	$(RM) *.so
	$(RM) *.o
	$(RM) poc
	$(RM) evtest
	make -C libremarkable clean
