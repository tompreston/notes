# List Dynamic Libraries
Ldd is use for where the libs are on the LD_LIBRARY_PATH. Otherwise we can use:

    objdump -p /path/program | grep NEEDED
