# Documentation

`node-sqlite3` has built-in function call serialization and automatically waits before executing a blocking action until no other action is pending. This means that it's safe start calling functions on the database object even if it is not yet fully opened. The `Database#close()` function will wait until all pending queries are completed before closing the database.

* [API documentation](https://github.com/developmentseed/node-sqlite3/wiki/API)
* [Query serialization/parallelization](https://github.com/developmentseed/node-sqlite3/wiki/Control-Flow)
* [Debugging](https://github.com/developmentseed/node-sqlite3/wiki/Debugging)
* [Extensions](https://github.com/developmentseed/node-sqlite3/wiki/Extensions)
* [Caching](https://github.com/developmentseed/node-sqlite3/wiki/Caching)
