#jackpot for gde  hello.bin

#history:
#2019 - Created by Fred Nora.

#todo:
#fazer um makefile pra compilar o shell
#obs: #bugbug tem que arrumas as coisas aqui.



VERSION = 0
PATCHLEVEL = 0
SUBLEVEL = 0
EXTRAVERSION =
#NAME = jackpot

#todo:
#We need to simplify these flags

CFLAGS = -m32 \
	--std=gnu89 \
	-nodefaultlibs \
	-nostdinc \
	-nostdlib \
	-static \
	-fgnu89-inline \
	-ffreestanding \
	-fno-builtin \
	-fno-pie \
	-no-pie \
	-fno-stack-protector \
	-s

#	-fleading-underscore \
#	-fno-stack-protector \
#	-s
	
	
#LIBC    = ../../lib/gdelibs/libc01/include/
#LIBCOBJ = ../../lib/gdelibs/libc01/obj
#API01   = ../../lib/gdelibs/api01/include/
#APIOBJ  = ../../lib/gdelibs/api01/obj


LIBC    = ../../lib/libc02/include/
LIBCOBJ = ../../lib/libc02/obj
API02   = ../../lib/api02/include/
APIOBJ  = ../../lib/api02/obj


	##
	## Objects
	##

myObjects = crt0.o \
main.o \
ctype.o \
stdio.o \
stdlib.o \
string.o \
time.o \
api.o \
unistd.o \
stubs.o    



.PHONY: all all-c jackpot-link finalize clean

all: main.o all-c jackpot-link finalize clean
	@echo "Ok?"

main.o:
	gcc  -c  main.c  $(CFLAGS) -I $(LIBC) -I $(API02) -o main.o

all-c:
	cp $(APIOBJ)/api.o      .
	
	cp $(LIBCOBJ)/ctype.o   .
	cp $(LIBCOBJ)/stdio.o .
	cp $(LIBCOBJ)/stdlib.o .
	cp $(LIBCOBJ)/string.o .
	cp $(LIBCOBJ)/time.o    .
	cp $(LIBCOBJ)/unistd.o  .
	cp $(LIBCOBJ)/stubs.o  .
	
#test
	cp $(LIBCOBJ)/crt0.o   .



jackpot-link:
	ld -m elf_i386 -T link.ld -o HELLO.BIN $(myObjects) -Map map.s

finalize:
	cp HELLO.BIN  ../../bin

clean:
	-rm *.o
	-rm HELLO.BIN 
	
	
