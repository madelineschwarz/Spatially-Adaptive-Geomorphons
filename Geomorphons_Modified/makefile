#!/usr/bin/env bash
# Path to the installed GDAL
#GDAL_PATH = /usr/local/Cellar/gdal/3.1.2 # path from OG source code

INCLUDE_PATH = /usr/include/gdal #${GDAL_PATH}/include
LIBS_PATH = /usr/lib 
GDAL_LIB = -lm -lgdal 

main: main.c utils.c geomorphons.c
#	gcc -I${INCLUDE_PATH} -L${LIBS_PATH} ${GDAL_LIB} main.c utils.c geomorphons.c -o geomorphons_modified -fopenmp
	gcc -I${INCLUDE_PATH} -L${LIBS_PATH} main.c utils.c geomorphons.c -o geomorphons_modified -fopenmp ${GDAL_LIB}
clean:
	rm main

