# Copyright (C) 2015-2017 Bayerische Motoren Werke Aktiengesellschaft (BMW AG)
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

Build instructions for Hello World example
------------------------------------------

## Linux Build Instructions

1. Build whole project at first:

```batch
cd <root directory of vSomeIP-Lib>$:
mkdir build
cd build
cmake ..
make
sudo make install
```

2. Build hello_world target
```batch
cd <root directory of vSomeIP-Lib>/examples/hello_world$:
mkdir build
cd build
cmake ..
make
```

## Windows Build Instructions

1. Build whole project at first:
```batch
cd <root directory of vSomeIP-Lib>
rmdir /s /q build
mkdir build
cd build
cmake .. -A x64 -DCMAKE_INSTALL_PREFIX="$YOUR_PATH"
cmake --build . --config Release
cmake --build . --config Release --target install
```

2. Build hello_world target:
```batch
cd <root directory of vSomeIP-Lib>/examples/hello_world
rmdir /s /q build
mkdir build
cd build
cmake .. -A x64 -DCMAKE_PREFIX_PATH="$YOUR_PATH"
cmake --build . --config Release
```

Note: Replace "Release" with "Debug" for debug builds.

Running Hello World Example
---------------------------

## Linux

The Hello World Example should be run on the same host.
The network addresses within the configuration files need to be adapted to match
the devices addresses.

To start the hello world client and service from their build-directory do:

HOST1:
```bash
VSOMEIP_CONFIGURATION=../helloworld-local.json \
VSOMEIP_APPLICATION_NAME=hello_world_service \
./hello_world_service
```

HOST1:
```bash
VSOMEIP_CONFIGURATION=../helloworld-local.json \
VSOMEIP_APPLICATION_NAME=hello_world_client \
./hello_world_client
```

## Windows

The Hello World Example should be run on the same host.
The network addresses within the configuration files need to be adapted to match
the devices addresses.

HOST1:
Note: You may need to define the path of the DLLs to run the examples
```batch
set "PATH=<root directory of vSomeIP-Lib>\build\Release;<root directory of vSomeIP-Lib>\build\test\common;<root directory of boost instalation>\lib64-msvc-14.2;%PATH%"
```
```batch
set "VSOMEIP_CONFIGURATION=<root directory of vSomeIP-Lib>\examples\hello_world\helloworld-local.json"
set "VSOMEIP_APPLICATION_NAME=hello_world_service"
cd /d <root directory of vSomeIP-Lib>\examples\hello_world\build\Release
hello_world_service.exe
```

HOST1:
Note: You may need to define the path of the DLLs to run the examples
```batch
set "PATH=<root directory of vSomeIP-Lib>\build\Release;<root directory of vSomeIP-Lib>\build\test\common;<root directory of boost instalation>\lib64-msvc-14.2;%PATH%"
```
```batch
set "VSOMEIP_CONFIGURATION=<root directory of vSomeIP-Lib>\examples\hello_world\helloworld-local.json"
set "VSOMEIP_APPLICATION_NAME=hello_world_client"
cd /d <root directory of vSomeIP-Lib>\examples\hello_world\build\Release
hello_world_client.exe
```

### Notes for Windows:
- Replace `<root directory of vSomeIP-Lib>` with your actual vsomeip-lib path
- Replace `$YOUR_PATH` with your actual installation path
- Replace "Release" with "Debug" for debug builds
- Both applications need to be running simultaneously for communication to work
- Ensure all paths match your actual installation directories

Expected output service
-----------------------
2023-11-03 16:40:31.974886 [info] Using configuration file: "../helloworld-local.json".
2023-11-03 16:40:31.013979 [info] Parsed vsomeip configuration in 17ms
2023-11-03 16:40:31.014674 [info] Configuration module loaded.
2023-11-03 16:40:31.014741 [info] Security disabled!
2023-11-03 16:40:31.014776 [info] Initializing vsomeip (3.4.9.1) application "hello_world_service".
2023-11-03 16:40:31.017415 [info] Instantiating routing manager [Host].
2023-11-03 16:40:31.018738 [info] create_routing_root: Routing root @ /tmp/vsomeip-0
2023-11-03 16:40:31.019573 [info] Application(hello_world_service, 4444) is initialized (11, 100).
2023-11-03 16:40:31.020057 [info] Starting vsomeip application "hello_world_service" (4444) using 2 threads I/O nice 255
2023-11-03 16:40:31.021469 [info] Client [4444] routes unicast:127.19.85.76, netmask:255.255.255.0
2023-11-03 16:40:31.021484 [info] main dispatch thread id from application: 4444 (hello_world_service) is: 7fbddd0a8640 TID: 311976
2023-11-03 16:40:31.032740 [info] Watchdog is disabled!
2023-11-03 16:40:31.022487 [info] shutdown thread id from application: 4444 (hello_world_service) is: 7fbddc8a7640 TID: 311977
2023-11-03 16:40:31.035423 [info] io thread id from application: 4444 (hello_world_service) is: 7fbdde144b80 TID: 311973
2023-11-03 16:40:31.036405 [info] vSomeIP 3.4.9.1 | (default)
2023-11-03 16:40:31.036308 [info] io thread id from application: 4444 (hello_world_service) is: 7fbdd77fe640 TID: 311979
2023-11-03 16:40:31.036751 [info] create_local_server: Listening @ /tmp/vsomeip-4444
2023-11-03 16:40:31.042149 [info] OFFER(4444): [1111.2222:0.0] (true)
2023-11-03 16:40:37.347127 [info] Application/Client 5555 is registering.
2023-11-03 16:40:37.350053 [info] Client [4444] is connecting to [5555] at /tmp/vsomeip-55552023-11-03 16:40:37.360259 [info] REGISTERED_ACK(5555)
2023-11-03 16:40:37.472179 [info] REQUEST(5555): [1111.2222:255.4294967295]
2023-11-03 16:40:37.494451 [info] RELEASE(5555): [1111.2222]
2023-11-03 16:40:37.497856 [info] Application/Client 5555 is deregistering.
2023-11-03 16:40:37.520884 [info] local_uds_client_endpoint_impl::receive_cbk Error: End of file
2023-11-03 16:40:37.611315 [info] Client [4444] is closing connection to [5555]
2023-11-03 16:40:41.330493 [info] vSomeIP 3.4.9.1 | (default)
2023-11-03 16:40:42.493762 [info] STOP OFFER(4444): [1111.2222:0.0] (true)

Expected output client
----------------------
2023-11-03 16:40:37.296486 [info] Using configuration file: "../helloworld-local.json".
2023-11-03 16:40:37.335551 [info] Parsed vsomeip configuration in 15ms
2023-11-03 16:40:37.336035 [info] Configuration module loaded.
2023-11-03 16:40:37.336107 [info] Security disabled!
2023-11-03 16:40:37.336144 [info] Initializing vsomeip (3.4.9.1) application "hello_world_client".
2023-11-03 16:40:37.336196 [info] Instantiating routing manager [Proxy].
2023-11-03 16:40:37.337152 [info] Client [5555] is connecting to [0] at /tmp/vsomeip-0
2023-11-03 16:40:37.337453 [info] Application(hello_world_client, 5555) is initialized (11, 100).
2023-11-03 16:40:37.337666 [info] Starting vsomeip application "hello_world_client" (5555) using 2 threads I/O nice 255
2023-11-03 16:40:37.338859 [info] main dispatch thread id from application: 5555 (hello_world_client) is: 7f1ff8197640 TID: 311983
2023-11-03 16:40:37.339940 [info] shutdown thread id from application: 5555 (hello_world_client) is: 7f1ff7996640 TID: 311984
2023-11-03 16:40:37.341120 [info] io thread id from application: 5555 (hello_world_client) is: 7f1ff8231b80 TID: 311982
2023-11-03 16:40:37.341294 [info] io thread id from application: 5555 (hello_world_client) is: 7f1ff7195640 TID: 311985
2023-11-03 16:40:37.343816 [info] create_local_server: Listening @ /tmp/vsomeip-5555
2023-11-03 16:40:37.345038 [info] Client 5555 (hello_world_client) successfully connected to routing  ~> registering..
2023-11-03 16:40:37.345108 [info] Registering to routing manager @ vsomeip-0
2023-11-03 16:40:37.358100 [info] Application/Client 5555 (hello_world_client) is registered.
2023-11-03 16:40:37.477528 [info] ON_AVAILABLE(5555): [1111.2222:0.0]
Sending: World
2023-11-03 16:40:37.478826 [info] Client [5555] is connecting to [4444] at /tmp/vsomeip-4444
Received: Hello World
2023-11-03 16:40:37.490189 [info] Stopping vsomeip application "hello_world_client" (5555).
2023-11-03 16:40:37.503150 [info] Application/Client 5555 (hello_world_client) is deregistered.
2023-11-03 16:40:37.508752 [info] Client [5555] is closing connection to [4444]
2023-11-03 16:40:37.508823 [info] local_uds_client_endpoint_impl::receive_cbk Error: Operation canceled
2023-11-03 16:40:37.508915 [info] local_uds_client_endpoint_impl::receive_cbk Error: Operation canceled
