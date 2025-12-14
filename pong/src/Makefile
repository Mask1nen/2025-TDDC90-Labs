#
# Makefile for pong, the vulnerable version of ping
#

#
# CC determines which compiler to use. You can include extra flags
# here as well.
#

# Stack protector DISABLED and executable stack (no DEP on stack)
CC = gcc -fno-stack-protector -z execstack

# Stack protector ENABLED (this is the default in gcc) and executable stack
#CC = gcc -fstack-protector -z execstack

# Stack protector DISABLED and DEP fully enabled (non-executable stack)
#CC = gcc -fno-stack-protector

#
# Compiler flags. You shouldn't need to change these at all
#
# -D_FORTIFY_SOURCE=0               Disable security hardening of some libc functions. Necessary for our trivial buffer overflow to work.
# -O0                               Standard optimization level
# -Wstrict-prototypes -Wall -W      Lotsa warnings
# -g                                Include debug info in the binary
#

CFLAGS=-D_FORTIFY_SOURCE=0 -O0 -Wstrict-prototypes -Wall -W -g

pong: Makefile ping.o ping_common.o
	$(CC) -o pong ping.o ping_common.o

clean:
	rm -f ping.o ping_common.o pong

install: pong
	cp pong /bin/pong
	chown root:root /bin/pong
	chmod 755 /bin/pong
	chmod +s /bin/pong

install11: pong
	cp pong /bin/pong.11
	chown root:root /bin/pong.11
	chmod 755 /bin/pong.11
	chmod +s /bin/pong.11

ping.o ping_common.o: Makefile ping_common.h
