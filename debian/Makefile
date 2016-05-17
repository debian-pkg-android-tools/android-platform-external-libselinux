NAME = libselinux
SOURCES = callbacks.c \
          check_context.c \
          freecon.c \
          init.c \
          label.c \
          label_file.c \
          label_android_property.c
SOURCES := $(foreach source, $(SOURCES), src/$(source))
CFLAGS += -DHOST
CPPFLAGS += -Iinclude
LDFLAGS += -fPIC -shared -Wl,-soname,$(NAME).so.0 -lpcre

build: $(SOURCES)
	$(CC) $^ -o $(NAME).so.0 $(CFLAGS) $(CPPFLAGS) $(LDFLAGS)
	ln -s $(NAME).so.0 $(NAME).so

clean:
	$(RM) *.so*