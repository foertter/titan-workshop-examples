matmul_1: matmul_1.CUF
ifneq "$(PE_ENV)" "PGI"
	@echo "Please swap to PrgEnv-pgi"
	@exit 1
endif
	ftn -ta=nvidia:4.1 -o matmul_1 matmul_1.CUF
.PHONY:
clean:
	rm -f *.o matmul_1 *.mod
