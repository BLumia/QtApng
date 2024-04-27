# QtApng

apng image plugin for Qt to support animated PNGs.

## Features

Enable the usage of apng images with Qt. The plugin adds the apng format as a new format for any Qt application, and thus supports loading of apng images via `QMovie`, `AnimatedImage` and other types.

### Embedded libpng/zlib

To build the plugin, libpng with the apng patch applied is required.

The project comes with a version of zlib and libpng (with the apng patch). They can be found in the `src/3rdparty` subfolder. They are automatically compiled into static libraries and used to link the apng plugin when neccessary. Please note that both libraries are compiled without any optimizations for architecture etc. If you wish to have those features, you can replace those two by your own versions.

 Project	| Version	| License																	| Project page
------------|-----------|---------------------------------------------------------------------------|--------------
 zlib		| 1.3.1		| [zlib-license](https://www.zlib.net/zlib_license.html)					| https://www.zlib.net/
 libpng		| 1.6.43	| [libpng-license](http://www.libpng.org/pub/png/src/libpng-LICENSE.txt)	| http://www.libpng.org/pub/png/libpng.html
 apng patch	| 1.6.43	| [libpng-license](http://www.libpng.org/pub/png/src/libpng-LICENSE.txt)	| https://sourceforge.net/projects/libpng-apng/

## Build manually

Regular CMake build steps applies:

```shell
$ cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release .
$ cmake --build build --config Release
```

The generated plugin name will be `qtapng`. You can then copy the plugin to Qt's `imageformats` plugin folder.

## Usage
Simply use the default Qt classes like `QImageReader`, `QMovie` etc. and open the apng files just like you would open normal images/animations (like gif files)

**Format Detection:**
Since the png format is already used by Qt, `*.png` files will **not** use the plugin. To load a png as animated, you can either rename the file to `*.apng`, or set the format explicitly

```cpp
QMovie movie("path/to/image.png", "apng");
```

## Note

1. This project is a fork of [Skycoder42/QtApng](https://github.com/Skycoder42/QtApng), which has been archived by the owner on Mar 4, 2023.
2. This fork is mainly serve for Qt 6. Building under Qt 5 might still work, but is not tested.
3. QMake build is NOT supported.