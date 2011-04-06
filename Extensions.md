# Extensions


## Database#loadExtension(path, [callback])

Loads a compiled SQLite extension into the database connection object.

* `path`: Filename of the extension to load.

* `callback` *(optional)*: If provided, this function will be called when the extension was loaded successfully or when an error occurred. The first argument is an error object. When it is `null`, loading succeeded. If no callback is provided and an error occurred, an `error` event with the error object as the only parameter will be emitted on the database object.

**Note: Make sure that the extensions you load are compiled or linked against the same version as `node-sqlite3` was compiled.** Version mismatches can lead to unpredictable behavior.