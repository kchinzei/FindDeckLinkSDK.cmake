This is an example of CMakeLists.txt using FindDeckLinkSDK.cmake.
By copying FindDeckLinkSDK.cmake and main.cpp (which is found in
DeviceList example of DeckLink SDK's Sample) into this folder,
you can build by:

 > cd (to this directory)
 > mkdir build
 > cd build
 > ccmake ..

You need to tell to ccmake where is your DeckLink SDK.
Once everything clear, you can:

 > make

and you should obtain executable 'myapp'!
