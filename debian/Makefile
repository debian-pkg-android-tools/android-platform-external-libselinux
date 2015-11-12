NAME = libselinux
SOURCES = callbacks.c \
          check_context.c \
          freecon.c \
          init.c \
          label.c \
          label_file.c \
          label_android_property.c
OBJECTS = $(SOURCES:.c=.o)
CFLAGS += -fPIC -c -DHOST
CPPFLAGS +=  -I../include
LDFLAGS += -fPIC -shared -Wl,-soname,$(NAME).so -lpcre

build: $(OBJECTS)
	cc $^ -o $(NAME).so $(LDFLAGS)
	ar rs $(NAME).a $^

clean:
	rm -f *.so *.a *.o

$(OBJECTS): %.o: %.c
	cc $< -o $@ $(CFLAGS) $(CPPFLAGS)