LUA_LIBDIR = /usr/local/lib/lua/5.1

CFLAGS += -Wall -Wextra --pedantic --std=c89
CFLAGS += `pkg-config --cflags lua5.3 dbus-1`
CFLAGS += -fPIC

OBJS = ldbus.o error.o pending_call.o connection.o bus.o message.o message_iter.o timeout.o watch.o

all:	ldbus.so

ldbus.so: $(OBJS)
	$(CC) -o ldbus.so -shared $(CFLAGS) $^ $(LDFLAGS)

clean:
	rm -f -- ldbus.so $(OBJS)

install: ldbus.so
	mkdir -p $(LUA_LIBDIR)
	cp ldbus.so $(LUA_LIBDIR)
