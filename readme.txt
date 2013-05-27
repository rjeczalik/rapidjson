Rapidjson v0.1
==============

Copyright (c) 2011 Milo Yip (miloyip@gmail.com)

http://code.google.com/p/rapidjson/

19 Nov 2011

### 1. Introduction

* Rapidjson is a JSON parser and generator for C++. It was inspired by rapidxml http://rapidxml.sourceforge.net/
* Rapidjson is small but complete. It supports both SAX and DOM style API. The SAX parser is only a half thousand lines of code.
* Rapidjson is fast. Its performance can be comparable to strlen(). It also optionally supports SSE2/SSE4.2 for acceleration.
* Rapidjson is self-contained. It does not depend on external libraries such as BOOST. It even does not depend on STL.
* Rapidjson is memory friendly. Each JSON value costs exactly 16/20 bytes for 32/64-bit machines (excluding text string). By default it uses a fast memory allocator, and the parser allocates memory compactly during parsing. 

For the full features please refer to the user guide.

JSON(JavaScript Object Notation) is a light-weight data exchange format.
More information about JSON can be obtained at
http://json.org/
http://www.ietf.org/rfc/rfc4627.txt

### 2. Installation

Rapidjson is a header-only C++ library. Just copy the rapidjson/include/rapidjson folder to system or project's include path.

To build the tests and examples,

* obtain premake4 http://industriousone.com/premake/download
* copy premake4 executable to rapidjson/build
* run rapidjson/build/premake.bat on Windows, rapidjson/build/premake on Linux or other platforms
* on Windows, build the solution at rapidjson/build/vs2008/ or /vs2010/
* on other platforms, run GNU make at rapidjson/build/gmake/ (e.g., make -f test.make config=release32, make -f example.make config=debug32)
* on success, the executable are generated at rapidjson/bin
