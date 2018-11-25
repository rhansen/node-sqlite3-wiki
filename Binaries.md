As of `v2.1.16` (and pull request [#192](https://github.com/developmentseed/node-sqlite3/pull/192)) `node-sqlite3` now defaults to installing a pre-built binary of `node_sqlite3.node` (with a statically linked `libsqlite3`) when available. As of `v2.2.0` (and pull request [#245](https://github.com/mapbox/node-sqlite3/pull/245)) the binary deployment system moved to using [node-pre-gyp](https://github.com/springmeyer/node-pre-gyp).

### Help

If you've landed here due to a failed install of `node-sqlite3` then feel free to create a [new issue](https://github.com/mapbox/node-sqlite3/issues/new) to ask for help. The most likely problem is that we do not yet provide pre-built binaries for your particular platform and so the `node-sqlite3` install attempted a source compile but failed because you are missing the [dependencies for node-gyp](https://github.com/TooTallNate/node-gyp#installation). But please provide as much detail on your problem as possible and we'll try to help. Please include:
 - terminal logs of failed install (best from running `npm install sqlite3 --loglevel=info`)
 - `node-sqlite3` version you tried to install
 - node version you are running
 - operating system and architecture you are running, e.g. `Windows 7 64 bit`.

### Background

The Node.js project [is discussing the design of a system for binary deployments](https://github.com/npm/npm/issues/1891) and a build farm for C++ modules like `node-sqlite3`. But since this does not exist yet we are leveraging [node-pre-gyp](https://github.com/springmeyer/node-pre-gyp) and S3 hosting.

### Forcing a source compile

To force building from source do:

```sh
npm install sqlite3 --build-from-source=sqlite3
```

or, if you are installing an app that depends on `sqlite3:

```sh
npm install --build-from-source=sqlite3
```

### Installing an alternative arch

To request an (additional) `arch` be installed that is different from the value of `process.arch` for your running node version you can pass `--target_arch`. For example, to install a 32bit binary on the 64 bit system do:

```sh
npm install sqlite3 --target_arch=ia32
```

### Missing binaries

We have not yet built binaries for all possible variants.

We can only support providing binaries for platforms which can be automated via a freely available continuous integration service. So we support windows via https://ci.appveyor.com and linux/osx via travis-ci.org.

### Binary versioning 

Binaries are versioned based on the `node-sqlite3` version, node version, platform, and architecture. Given this amounts to many versions we have not yet created binaries for all possible combinations.

For more info about the versioning see https://github.com/mapbox/node-pre-gyp#versioning

For info about how node versions crosswalk with their ABI version see:
 - https://github.com/mapbox/node-pre-gyp/blob/master/lib/util/abi_crosswalk.json
 - https://nodejs.org/download/release/index.json
 - https://github.com/mapbox/node-pre-gyp/blob/master/scripts/abi_crosswalk.js

## Code implementation

See https://github.com/springmeyer/node-pre-gyp
