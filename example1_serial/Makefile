CC=cc
FC=ftn
CUDAC=nvcc
CUDACFLAGS=-arch=sm_20 --ptxas-options=-v
CUDAF=${FC}
CUDAFFLAGS=-Mcuda=cc20,ptxinfo,cuda3.2 -ta=nvidia:cc20,time -Minfo=all

all: cudaf.exe cudac.exe

cudaf.exe: scaleitF.o
	${CUDAF} -o $@ ${CUDAFFLAGS} $<

cudac.exe: scaleitC.o
	${CUDAC} -o $@ ${CUDACFLAGS} $<

.PHONY: clean
clean: 
	-rm -f *.o *.cub *.ptx *.lst *.mod cudaf.exe cudac.exe

.SUFFIXES: .o .F90 .c .cu
.F90.o:
	$(FC) -c $(CUDAFFLAGS) $(FFLAGS) -o $*.o $<
.c.o:
	$(CC) -c $(CFLAGS) -o $*.o $<
.cu.o:
	$(CUDAC) -c $(CUDACFLAGS) $(CFLAGS) -o $*.o $<