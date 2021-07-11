CFLAGS += -fPIC -g
CFLAGS += -std=c99

SOURCES = fb.c refresh.c serde.c bitmap.c freetype.c
OBJECTS = $(SOURCES:.c=.o)
FREETYPE_PATH = ../libfreetype/install

all: static shared

shared: $(OBJECTS)
	$(CC) -shared $(CCFLAGS) $(OBJECTS) $(LDFLAGS) -o libremarkable.so

static: $(OBJECTS)
	$(AR) -rsc libremarkable.a $(OBJECTS) $(LDFLAGS)

%.o: %.c
	$(CC) -c $(CFLAGS) $< -o $@

clean:
	$(RM) *.o
	$(RM) *.so
	$(RM) *.a
