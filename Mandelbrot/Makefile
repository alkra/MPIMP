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
mandel.od: mandel.c rasterfile.h
	mpicc -c -g -Wall -Wextra mandel.c

mandel.o: mandel.c rasterfile.h
	mpicc -c -O mandel.c


# Link
release: mandel.o
	mpicc -o mandel.akraus mandel.o -lm

debug: mandel.od
	mpicc -o mandel.akraus mandel.o -lm

# Run


# Clean
clean:
	-rm mandel.akraus mandel.o

rebuild: clean debug

.PHONY : mandel.od release debug clean rebuild

