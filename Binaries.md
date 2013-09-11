As of `v2.1.16` (and pull request [#192](https://github.com/developmentseed/node-sqlite3/pull/192)) `node-sqlite3` now defaults to installing a pre-built binary of `node_sqlite3.node` (with a statically linked `libsqlite3`) when available.


### Forcing a source compile

To force building from source do:

```sh
npm install sqlite3 --build-from-source=sqlite3
```

or 

```sh
npm install sqlite3 --build-from-source
```

### Installing an alternative arch

To request an (additional) `arch` be installed that is different from the value of `process.arch` for your running node version you can pass `--target_arch`. For example, to install a 32bit binary on the 64 bit system do:

```sh
npm install sqlite3 --target_arch=ia32
```

### Missing binaries

We have not yet built binaries for all possible variants. Here are the ones that are most requested and not available as of `Sept 10, 2013`:

<img src="https://raw.github.com/wiki/developmentseed/node-sqlite3/404-binaries.png"/>

### Creating new binaries

Users that find a binary is not available for their platform are encouraged to trigger a custom source compile that will package a binary for later distribution. To do this run:

```sh
npm install sqlite3 --stage
```

This will drop a tarball (`.tar.gz`) and a shasum (`sha1.txt`) in the `stage/` folder within the installed module folder. These two files therefore will be available at `$HOME/node_modules/sqlite3/stage/Release/`.

You can also run `npm install --stage` from within a `node-sqlite3` checkout from github.

To submit your built `tar.gz` please email it to dane - at - mapbox.com. In the future we plan to automate this.

### Available binaries

Currently available binaries [are listed here](http://node-sqlite3.s3.amazonaws.com/index.html?path=Release/).

### Binary versioning 

Binaries are versioned based on the `node-sqlite3` version, node version, platform, and architecture. Given this amounts many versions we have not yet created binaries for all possible combinations.

Specifically, versioning works like this:

```sh
${configuration folder}/node-sqlite3-${MAJOR}.${MINOR}.${ABI}-node-v${ABI}-${platform}-${arch}.tar.gz
```
 - configuration folder - 'Release' or 'Debug'
 - node-sqlite3 `MAJOR` and `MINOR` match the semver values for the given release. The `ABI` is a special incrementing letter that marks new versions of the c++ code.
 - The node versioning uses the C++ `ABI` number rather node's semver string. This value is available in javascript `process.versions.modules` as of [`>= v0.10.4 >= v0.11.7`](https://github.com/joyent/node/commit/ccabd4a6fa8a6eb79d29bc3bbe9fe2b6531c2d8e) and in C++ as the `NODE_MODULE_VERSION` define much earlier. Currently the `node-sqlite3` build scripts access this value only via `process.versions.modules` so for versions before `v0.10.4` the `v8` `MAJOR.MINOR` is used as a proxy.
 - `platform` matches node's `process.platform` like `linux`, `darwin`, and `win32`
 - `arch` matches node's `process.arch` like `x64` or `ia32`


### Crosswalking node version to node module ABI

Below is a listing of how node versions crosswalk with the `process.versions.modules` value:

```js
{ '0.6.3': 1,
  '0.6.4': 1,
  '0.6.5': 1,
  '0.6.6': 1,
  '0.6.7': 1,
  '0.6.8': 1,
  '0.6.9': 1,
  '0.6.10': 1,
  '0.6.11': 1,
  '0.6.12': 1,
  '0.6.13': 1,
  '0.6.14': 1,
  '0.6.15': 1,
  '0.6.16': 1,
  '0.6.17': 1,
  '0.6.18': 1,
  '0.6.19': 1,
  '0.6.20': 1,
  '0.6.21': 1,
  '0.7.0': 1,
  '0.7.1': 1,
  '0.7.2': 1,
  '0.7.3': 1,
  '0.7.4': 1,
  '0.7.5': 1,
  '0.7.6': 1,
  '0.7.7': 1,
  '0.7.8': 1,
  '0.7.9': 1,
  '0.7.10': 1,
  '0.7.11': 1,
  '0.7.12': 1,
  '0.8.0': 1,
  '0.8.1': 1,
  '0.8.2': 1,
  '0.8.3': 1,
  '0.8.4': 1,
  '0.8.5': 1,
  '0.8.6': 1,
  '0.8.7': 1,
  '0.8.8': 1,
  '0.8.9': 1,
  '0.8.10': 1,
  '0.8.11': 1,
  '0.8.12': 1,
  '0.8.13': 1,
  '0.8.14': 1,
  '0.8.15': 1,
  '0.8.16': 1,
  '0.8.17': 1,
  '0.8.18': 1,
  '0.8.19': 1,
  '0.8.20': 1,
  '0.8.21': 1,
  '0.8.22': 1,
  '0.8.23': 1,
  '0.8.24': 1,
  '0.8.25': 1,
  '0.9.0': 1,
  '0.9.1': 10,
  '0.9.2': 10,
  '0.9.3': 10,
  '0.9.4': 10,
  '0.9.5': 10,
  '0.9.6': 10,
  '0.9.7': 10,
  '0.9.8': 10,
  '0.9.9': 11,
  '0.9.10': 11,
  '0.9.11': 11,
  '0.9.12': 11,
  '0.10.0': 11,
  '0.10.1': 11,
  '0.10.2': 11,
  '0.10.3': 11,
  '0.10.4': 11,
  '0.10.5': 11,
  '0.10.6': 11,
  '0.10.7': 11,
  '0.10.8': 11,
  '0.10.9': 11,
  '0.10.10': 11,
  '0.10.11': 11,
  '0.10.12': 11,
  '0.10.13': 11,
  '0.10.14': 11,
  '0.10.15': 11,
  '0.10.16': 11,
  '0.10.17': 11,
  '0.10.18': 11,
  '0.11.0': 12,
  '0.11.1': 12,
  '0.11.2': 12,
  '0.11.3': 12,
  '0.11.4': 12,
  '0.11.5': 12,
  '0.11.6': 12,
  '0.11.7': 12 }
```

## Code implementation

- `package.json` has an `install` target that points at [`./build.js`](https://github.com/developmentseed/node-sqlite3/blob/master/build.js)
- `build.js` can be run directly but will also properly handle arguments passed to `npm install`
- A small module called [`binary_name.js`](https://github.com/developmentseed/node-sqlite3/blob/master/lib/binary_name.js) is used both in `build.js` and [`lib/sqlite3.js`](https://github.com/developmentseed/node-sqlite3/blob/master/lib/sqlite3.js#L1-L8) to abstract out the details of what a given binary build is called and where it lives.
- Binaries are checked for on s3 and if not found a source compile will be the fallback
- sha1 sums are used to validate binaries before testing
- a naive test of whether the module can be required is done and a source compile is the fallback if this fails
- generally this code is quite rough - I plan (@springmeyer) to clean it up eventually into a stand alone module any developer of a C++ addon could use and contribute to.
- A few scripts live in [build-util](https://github.com/developmentseed/node-sqlite3/tree/master/build-util) that I use to rebuild binaries on mac and upload them to s3 - this will be cleaned up and integrated into js eventually