NAME = libselinux
SOURCES = callbacks.c \
          check_context.c \
          freecon.c \
          init.c \
          label.c \
          label_file.c \
          label_android_property.c
OBJECTS = $(SOURCES:.c=.o)
INCLUDES = -I. -I../include
LOCAL_CFLAGS = -fPIC -c -DHOST
LOCAL_LDFLAGS = -fPIC -shared -rdynamic -lpthread -lpcre

build: $(OBJECTS)
	cc $^ -o $(NAME).so.$(UPSTREAM_VERSION) -Wl,-soname,$(NAME).so.5 $(LDFLAGS) $(LOCAL_LDFLAGS)
	ar rs $(NAME).a $^

clean:
	rm -f *.so.* *.a *.o

$(OBJECTS): %.o: %.c
	cc $< -o $@ $(CFLAGS) $(CPPFLAGS) $(INCLUDES) $(LOCAL_CFLAGS)