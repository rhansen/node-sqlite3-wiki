Disclaimer: Running Node.js with node-sqlite3 on Android is experimental and not supported by the official maintainers.
It is assumed that you know how to compile Node.js for Android, have a copy of the Android-NDK
and a rooted Android device or use the emulator.

At the moment there is no official Android support in Node.js,
however, you may have encountered the android-configure script.
With it, one can cross compile Node.js to arm-v5.
Now, if you want to use node-sqlite3 with your Android Node.js, you will run into problems.
First, you will need to cross compile node-sqlite3.
Second Android is very restrictive about loading shared libraries, which complicates things.
The easiest way found so far, has been to compile node-sqlite3 into Node.js as a core module.
For this, you just have to copy the node-sqlite3 files into the appropriate places in the Node.js dir
and make Node.js aware of the module by adding it to the node.gyp file and adding "NODE_EXT_LIST_ITEM(node_sqlite3)" to the node_extensions.h.

This has been tested with Android-NDK-r8e, Node.js v0.10.18 and node-sqlite3 v2.1.14.