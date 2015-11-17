NAME = libselinux
SOURCES = callbacks.c \
          check_context.c \
          freecon.c \
          init.c \
          label.c \
          label_file.c \
          label_android_property.c
SOURCES := $(foreach source, $(SOURCES), src/$(source))
OBJECTS = $(SOURCES:.c=.o)
CFLAGS += -fPIC -c -DHOST
CPPFLAGS += -Iinclude
LDFLAGS += -fPIC -shared -Wl,-soname,$(NAME).so.$(ANDROID_SOVERSION) -lpcre

build: $(OBJECTS)
	$(CC) $^ -o $(NAME).so.$(ANDROID_LIBVERSION) $(LDFLAGS)
	$(AR) rs $(NAME).a $^
	ln -s $(NAME).so.$(ANDROID_LIBVERSION) $(NAME).so
	ln -s $(NAME).so.$(ANDROID_LIBVERSION) $(NAME).so.$(ANDROID_SOVERSION)

clean:
	$(RM) $(OBJECTS) *.so* *.a

$(OBJECTS): %.o: %.c
	$(CC) $< -o $@ $(CFLAGS) $(CPPFLAGS)