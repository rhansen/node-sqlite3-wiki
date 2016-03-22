Binaries are available of node-sqlite3 for windows, so you:

 - do not need to compile yourself
 - you also then do not need visual studio compiler or python

See https://github.com/mapbox/node-sqlite3/wiki/Binaries for how things work with binaries.

If you want to source compile, or if you are running a custom node version for which we do not provide binaries for then read on:

## 1. Install Node

Make sure you have the latest stable release of node - at the time of writing that is either v0.10.x or v4.

NOTE: be aware of whether you installed the 32 bit or 64 bit version of Node.

## 1. Install Visual Studio with C++ compiler

You need to install the same visual studio version that the node.exe you are using was built with. Because this changes, we do not document that version here.

## 3. Install Python

A STABLE version of Python is required to build sqlite3 for windows. Download it from <https://www.python.org/downloads/windows/>. Do not forget to add the Python install directory to your system PATH.
* Tested and functional with Python 2.7.9. 
* Tested but not working with Python 3.5.0a1

## 4. Build the module

Type:

    npm install sqlite --build-from-source

Or download the git repo and inside the repo type:

    npm install --build-from-source

Note: `--build-from-source` is an option understood by https://github.com/mapbox/node-pre-gyp and it triggers a source compile instead of installation from pre-compiled binaries.

## 5. Troubleshooting

Create an issue if you have trouble. Please provide as much detail about what versions you are using and the exact errors you encountered.
