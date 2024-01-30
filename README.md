# Evaluation-of-a-Spatially-Adaptive-Approach-
Codes from Paper titled "Evaluation of a Spatially Adaptive Approach for Land Surface Classification from Digital Elevation Models" published in International Journal of Geographical Information Science  

Maria Dekavalla & Demetre Argialas (2017) Evaluation of a spatially adaptive approach for land surface classification from digital elevation models, International Journal of Geographical Information Science, 31:10, 1978-2000, DOI: 10.1080/13658816.2017.1344984 

original code: https://github.com/mariadek/Evaluation-of-a-Spatially-Adaptive-Approach-

# System set-up
1) Clone repository
2) Open repository in VSCode dev env container: Debian
3) Install python 3.8 in dev env:
```
  sudo apt-get update
  sudo apt-get install build-essential
  sudo apt-get install python3-dev
  sudo apt-get install libcurl4-gnutls-dev libexpat1-dev libproj-dev libgeos-dev libsqlite3-dev
```
5) Install gdal 3.2.1 in dev env:
  ```
   sudo apt-get update
   sudo apt-get install gdal-bin libgdal-dev
   # check gdal installation
   gdalinfo --version
 ```
   
7) Verify the paths to gdal includes ("gdal.h" & "cpl_error.h") and gdal libraries (libgdal.so, etc.) match path in makefile:
   ```
   ls /usr/include/gdal
   ls /usr/lib
   ```
   ![image](https://github.com/madelineschwarz/Spatially-Adaptive-Geomorphons/assets/60195170/c096a804-c62a-4f2e-a0df-3499aa3b4713)
9) Build the C code:
    ```
   cd Geomorphons_Modified
   make
    ```
11) Compute the ternary pattern, higher cells (0-8), and lower cells (0-8) of a DEM (tif format works)
```
   # Execution: ./geomorphons_modified <input> <output1> <output2> <output3>
   ./geomorphons_modified zap_5mDEM.tif ternary.tif higher.tif lower.tif   # example using test data (USGS 3dep 2011 Sangres)
```
## General Notes
- Use <5m-resolution DEM
- conda env gdal configuration does not work well
- geomorphons_modified is compatible with .tif -- ESRI BIL files are not compatible
- morphometric_parameters.c is compatible with .asc files -- running into Segmentation Fault error
    Convert .tif to .asc with gdal:
  ```
  gdal_translate -of AAIGrid input.tif output.asc
  
  ```
  


   
