# wgpu-native

These are just some pre-built libraries of wgpu-native.

It is easier to compile and link to the rust libraries than it is to create and maintain a bazel
build system for the wgpu-native project. Having this is a separate repository makes it easier for
multiple projects to fetch it and use it, as well as allowing the repos containing those projects to
be smaller.


## Usage:

Add the following to the `WORKSPACE.bazel` file in the base of your source repo:
```
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# wgpu-native

_WGPU_VERSION = "0.15.1.2"

http_archive(
    name = "wgpu",
    strip_prefix = "wgpu-native-lib-{version}".format(version = _WGPU_VERSION),
    url = "https://github.com/nullcatalyst/wgpu-native-lib/archive/refs/tags/v{version}.tar.gz".format(version = _WGPU_VERSION),
)
```

Add the library and header files as dependencies to your existing targets:
```
cc_library(
    name = "my_cool_game",
    srcs = [
        ...
    ],
    deps = [
        "@wgpu//:hdrs",
        "@wgpu//:lib-windows-x86_64",
    ],
)
```
