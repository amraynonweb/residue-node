                   ‫بسم الله الرَّحْمَنِ الرَّحِيمِ

# Residue NodeJS Client
A very simple, secure NodeJS library to interact with residue seamlessly.

This module provides interface for connecting and interacting with residue server seamlessly, means, once you are connected this module takes care of expired tokens and clients and keep itself updated with latest tokens and ping server when needed to stay alive.

[![Version](https://img.shields.io/npm/v/residue.svg)](https://www.npmjs.com/package/residue)

## Native API
This library depends on following native modules, without them library will not work:

 * [Crypto Module](https://nodejs.org/api/crypto.html)
 * [ZLib Module](https://nodejs.org/api/zlib.html)
 * [Net Module](https://nodejs.org/api/net.html)

## API
#### `connect(options)`
Connects application to residue using params. If options is not specified, you should use `loadConfiguration` to load the options

Valid options are:

```
{
    url: "<host_where_residue_server_is_listening>:<residue_connection_port>",
    access_codes: [
        {
             ... logger_id and code
        }
    ],
    application_id: <app_name [optional]>,
    rsa_key_size: <key_size_for_initial_final_key_transmission [optional]>,
    utc_time: <whether_to_use_UTC_time [optional]>,
    time_offset: <time_offset_in_seconds [optional]>,
    client_id: <client_id_that_server_knows_you_as [optional]>,
    client_private_key: <full_path_of_private_key> [must be provided with client_id],
    server_public_key: <full_path_of_server_public_key>
}
```

Please refer to [`loadConfiguration`](https://muflihun.github.io/residue/docs/class_residue.html#a8292657c93a775b6cbf22c6d4f1166f4) in our C++ library's documentation for more details.

#### `loadConfiguration(jsonFilename)`
Loads configurations / options via json file. Returns true if successfully loaded, otherwise false.

This does not verify the options. Options are validated in `connect()` function

#### `getLogger(logger_id)`
Returns logger class for logging interface

## Sample
You can check out [sample client apps](https://github.com/muflihun/residue-node/blob/master/samples) for practical use of this package.