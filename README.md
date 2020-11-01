### Download prebuilt dependencies for MinGW 32bit build: [prebuilt_dep_mingw_32bit.zip](https://github.com/viewizard/astromenace-windows-prebuilt-dependencies/releases/download/latest/prebuilt_dep_mingw_32bit.zip)
Based on lib's sources and binary packages available for download from `Releases` page.

#### OpenAL (bin)
https://openal-soft.org/#download

#### SDL2 (bin)
https://www.libsdl.org/download-2.0.php

#### libogg and libvorbis (sources)
https://xiph.org/downloads/

#### freealut (sources)
https://github.com/vancegroup/freealut

#### freetype (sources)
https://sourceforge.net/projects/freetype/files/

### Build

`patches_for_msys2_mingw_32bit_build` contain patches, that were used for libs build. Note, I used absolute paths from my PC, make sure you correct them.

Build commands (MSYS2 + MinGW 32bit) for freealut, libogg and libvorbis:
```
$ mkdir build
$ cd build
$ cmake .. -G Ninja -DCMAKE_INSTALL_PREFIX=$PWD/../bin -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=true
$ cmake --build . --target install
```
Build commands (MSYS2 + MinGW 32bit) for freetype:
```
$ mkdir build
$ cd build
$ cmake .. -G Ninja -DCMAKE_INSTALL_PREFIX=$PWD/../bin -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=true \
-DCMAKE_DISABLE_FIND_PACKAGE_ZLIB=TRUE \
-DCMAKE_DISABLE_FIND_PACKAGE_BZip2=TRUE \
-DCMAKE_DISABLE_FIND_PACKAGE_PNG=TRUE \
-DCMAKE_DISABLE_FIND_PACKAGE_HarfBuzz=TRUE \
-DCMAKE_DISABLE_FIND_PACKAGE_BrotliDec=TRUE
$ cmake --build . --target install
```

