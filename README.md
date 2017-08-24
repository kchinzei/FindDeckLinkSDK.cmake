# FindDeckLinkSDK.cmake - Cmake module to find DeckLink SDK

This is a cmake module to find where the DeckLink SDK include file is installed.
DeckLink SDK is the toolkit for BlackMagick Design Capture hardware.

This code sets the following variables:
```
  DeckLinkSDK_FOUND    = DeckLinkSDK is found.
  DeckLinkSDK_PATH     = where DeckLinkSDK is. Cashed.
  DeckLinkSDK_INCLUDE_PATH = path to where ${DeckLinkSDK_INCLUDE_FILE} is found.
  DeckLinkSDK_INCLUDE_FILE = DeckLinkAPI.idl (Win) or DeckLinkAPI.h (Mac/Linux).
  DeckLinkSDK_SRC_FILE = full path to DeckLinkAPIDispatch.cpp (Mac/Linux) or empty (Win).
  DeckLinkSDK_LIBS     = external libraries to link for target.
  DeckLinkSDK_DEF      = additional compiler flags.
```

If a system environment variable either of `DECKLINK_SDK_DIR`,
`BLACKMAGIC_SDK_DIR`, `DECKLINK_DIR` or `BLACKMAGIC_DIR` set, it looks
at paths from it.

Typical CmakeLists.txt snippet is;
```cmake
    FIND_PACKAGE(DeckLinkSDK REQUIRED)
    IF(DeckLinkSDK_FOUND)
      INCLUDE_DIRECTORIES("${DeckLinkSDK_INCLUDE_PATH}")
      IF   (COMPILE_DEFINITIONS)
        SET(COMPILE_DEFINITIONS "${COMPILE_DEFINITIONS};${DeckLinkSDK_DEF}")
      ELSE (COMPILE_DEFINITIONS)
        SET(COMPILE_DEFINITIONS ${DeckLinkSDK_DEF})
      ENDIF(COMPILE_DEFINITIONS)
      ADD_EXECUTABLE(${your_app} ${your_srcs} "${DeckLinkSDK_SRC_FILE}")
      TARGET_LINK_LIBRARIES(${your_app} ${your_libs} "${DeckLinkSDK_LIBS}")
    ENDIF(DeckLinkSDK_FOUND)
```
You do the following in your DeckLink related sources;
```c
    #include "DeckLinkSDK.h"
```
You can optionally provide version argument, for example;
```cmake
    FIND_PACKAGE(DeckLinkSDK 10.5 REQUIRED)
```
will ensure the version of the SDK is greater than or equal to 10.5 (e.g., 10.4.99 will produce an error.)

## Links
[Blackmagic Design](https://www.blackmagic-design.com/support "where
DeckLink SDK found")
[Cmake.org](https://cmake.org "Cross platform build tool")
