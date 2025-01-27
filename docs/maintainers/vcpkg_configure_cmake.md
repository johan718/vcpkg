# vcpkg_configure_cmake

Configure CMake for Debug and Release builds of a project.

## Usage
```cmake
vcpkg_configure_cmake(
    SOURCE_PATH <${SOURCE_PATH}>
    [PREFER_NINJA]
    [DISABLE_PARALLEL_CONFIGURE]
    [GENERATOR <"NMake Makefiles">]
    [OPTIONS <-DUSE_THIS_IN_ALL_BUILDS=1>...]
    [OPTIONS_RELEASE <-DOPTIMIZE=1>...]
    [OPTIONS_DEBUG <-DDEBUGGABLE=1>...]
)
```

## Parameters
### SOURCE_PATH
Specifies the directory containing the `CMakeLists.txt`. By convention, this is usually set in the portfile as the variable `SOURCE_PATH`.

### PREFER_NINJA
Indicates that, when available, Vcpkg should use Ninja to perform the build. This should be specified unless the port is known to not work under Ninja.

### DISABLE_PARALLEL_CONFIGURE
Disables running the CMake configure step in parallel.

This is needed for libraries which write back into their source directory during configure.

### GENERATOR
Specifies the precise generator to use.

This is useful if some project-specific buildsystem has been wrapped in a cmake script that won't perform an actual build. If used for this purpose, it should be set to "NMake Makefiles".

### OPTIONS
Additional options passed to CMake during the configuration.

### OPTIONS_RELEASE
Additional options passed to CMake during the Release configuration. These are in addition to `OPTIONS`.

### OPTIONS_DEBUG
Additional options passed to CMake during the Debug configuration. These are in addition to `OPTIONS`.

## Notes
This command supplies many common arguments to CMake. To see the full list, examine the source.

## Examples

* [zlib](https://github.com/Microsoft/vcpkg/blob/master/ports/zlib/portfile.cmake)
* [cpprestsdk](https://github.com/Microsoft/vcpkg/blob/master/ports/cpprestsdk/portfile.cmake)
* [poco](https://github.com/Microsoft/vcpkg/blob/master/ports/poco/portfile.cmake)
* [opencv](https://github.com/Microsoft/vcpkg/blob/master/ports/opencv/portfile.cmake)

## Source
[scripts/cmake/vcpkg_configure_cmake.cmake](https://github.com/Microsoft/vcpkg/blob/master/scripts/cmake/vcpkg_configure_cmake.cmake)
