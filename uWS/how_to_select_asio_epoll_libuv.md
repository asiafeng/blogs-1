## uWS如何选择网络库

在src/Backend.h中有以下定义：
``` c++
#ifndef BACKEND_H
#define BACKEND_H

// Default to Epoll if nothing specified and on Linux
// Default to Libuv if nothing specified and not on Linux
#ifdef USE_ASIO
#include "Asio.h"
#elif !defined(__linux__) || defined(USE_LIBUV)
#include "Libuv.h"
#else
#define USE_EPOLL
#include "Epoll.h"
#endif

#endif // BACKEND_H
```
在编译中，因为是在  uWebsockets目录下直接 make，ubuntu下所使用的是 Epoll。
