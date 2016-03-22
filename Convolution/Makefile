# © Alban Kraus 2016
# École nationale des sciences géographiques
# 6-8 avenue Blaise Pascal - Champs-sur-Marne
# 77455 MARNE-LA-VALLÉE CEDEX 2
#
# TP de Ahmad Audi
#
# This is the Makefile

# Default target
default: release

# Project

# Compilation
convol.od: convol.c rasterfile.h
	mpicc -c -g -Wall -Wextra convol.c

convol.o: convol.c rasterfile.h
	mpicc -c -O convol.c


# Link
release: convol.o
	mpicc -o convol.akraus convol.o -lm

debug: convol.od
	mpicc -o convol.akraus convol.o -lm

# Run


# Clean
clean:
	-rm convol.akraus convol.o

rebuild: clean debug

.PHONY : convol.od release debug clean rebuild

