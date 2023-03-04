# wgpu-native

These are just some pre-built libraries of wgpu-native.

It is easier to compile and link to the rust libraries than it is to create and maintain a bazel
build system for the wgpu-native project. Having this is a separate repository makes it easier for
multiple projects to fetch it and use it, as well as allowing the repos containing those projects to
be smaller.
