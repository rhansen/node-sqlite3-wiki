**NOTE:** Requires Visual Studio 2010. I didn't test with the Express version, but it *should* do.

## 1. Install Visual Studio 2010 with C++ compiler

<http://www.microsoft.com/visualstudio/eng/products/visual-studio-express-products>

Note: Microsoft is always changing the names of things so it is hard to know exactly what is needed. If you get through these install steps successfully please edit this wiki with how you set up Visual Studio.

Note: you may also need the Win SDK <http://www.microsoft.com/en-us/download/details.aspx?displayLang=en&id=8279>

Note: Another link to Visual Studio 2010 (`wdexpress_full.exe`) is <http://go.microsoft.com/?linkid=9816758>

## 2. Install Node

Make sure you have the latest node - either v0.8.x or v0.10.x. v0.10.x is ideal since it will contain the latest `node-gyp`. `node-gyp` is critical for building `node-sqlite3`.

You can use the precompiled binaries/easy installers or you can build node yourself. Just be aware that `node-gyp` prefers the precompiled installer the provides a stable release. If you build a development version of node from source `node-gyp` will complain about needing to know the path to the headers. 

NOTE: be aware of whether you installed the 32 bit or 64 bit version of Node.

## 3. Install Python

A STABLE version of Python is required to build sqlite3 for windows. Download it from <https://www.python.org/downloads/windows/>. Do not forget to add the Python install directory to your system PATH.
* Tested and functional with Python 2.7.9. 
* Tested but not working with Python 3.5.0a1

## 4. Build the module

Type:

    npm install sqlite


Or download the git repo and inside the repo type:

    npm install

TIP: to avoid full recompiles you can install `node-gyp` globally and just do:

    node-gyp configure build

## 5. Troubleshooting

Create an issue if you have trouble. Please provide as much detail about what versions you are using and the exact errors you encountered.
