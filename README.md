# Install building tools
Before building, ensure to download and install these tools in the build environment to the default place.

[ For WIN 32 bit ]

perl http://downloads.activestate.com/ActivePerl/releases/5.24.1.2402/ActivePerl-5.24.1.2402-MSWin32-x86-64int-401627.exe
cmake https://cmake.org/files/v3.8/cmake-3.8.0-win32-x86.msi

[ For WIN 64 bit ]

Perl64 http://downloads.activestate.com/ActivePerl/releases/5.24.2.2403/ActivePerl-5.24.2.2403-MSWin32-x64-403863.exe
cmake64 https://cmake.org/files/v3.10/cmake-3.10.0-win64-x64.msi


# Build OpenSSL
Download openssl-1.0.2k.zip to your workspace and extract it to the directory %workspace%\OpenSSL\src\openssl
Navigate to the directory and generate the VS2010 solution with cmake.

[ For WIN 32 bit ]

cd %workspace%\OpenSSL\src\openssl

perl Configure VC-WIN32 no-asm no-rc5 --prefix=%workspace%\OpenSSL\WIN32

ms\do_ms

nmake -f ms\ntdll.mak

nmake -f ms\ntdll.mak install

[ For WIN 64 bit ]

cd %workspace%\OpenSSL\src\openssl

perl Configure VC-WIN64A no-asm no-rc5 --prefix=%workspace%\OpenSSL\WIN64

ms\do_win64a

nmake -f ms\ntdll.mak

nmake -f ms\ntdll.mak install

More details, please see: http://blog.csdn.net/henter/article/details/8364532

[Note] There is a different way to build the OpenSSL 1.1.0 version. More details, see
http://p-nand-q.com/programming/windows/building_openssl_with_visual_studio_2013.html
https://github.com/openssl/openssl/blob/master/INSTALL#L44
