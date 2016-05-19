# Kitura-Session-Redis
Kitura-Session store using Redis as the backing store


![Mac OS X](https://img.shields.io/badge/os-Mac%20OS%20X-green.svg?style=flat)
![Linux](https://img.shields.io/badge/os-linux-green.svg?style=flat)
![Apache 2](https://img.shields.io/badge/license-Apache2-blue.svg?style=flat)

## Summary
 [Kitura-Session](https://github.com/IBM-Swift/Kitura-Session) store using Redis as backing store

## Table of Contents
* [Swift version](#swift-version)
* [Example](#example)
* [License](#license)

## Swift version
The latest version of Kitura-Credentials works with the DEVELOPMENT-SNAPSHOT-2016-05-03-a version of the Swift binaries. You can download this version of the Swift binaries by following this [link](https://swift.org/download/). Compatibility with other Swift versions is not guaranteed.


## Example
In order to use Redis as session store, create an instance of `RedisStore`, and pass it to `Session` constructor.

```swift
import KituraSession
import KituraSessionRedis

let redisStore = RedisStore(redisHost: host, redisPort: port, redisPassword: password)
let session = Session(secret: "Very very secret.....", store: redisStore)
```

Now call `setupRedis` method to connect to Redis. Pass your code for router setup as a callback.

```swift  
redisStore.setupRedis() { error in
    guard (error == nil) else {
        // Error
    }

    router.all(middleware: session)

    router.post(<path>) {
      ...
    }

    router.get(<path>) {
      ...
    }                
}

```


## License
This library is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE.txt).
