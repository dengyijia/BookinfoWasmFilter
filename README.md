This is an example of how to build and deploy WASM filter on envoy locally. Before executing the commands to build and deploy the filter, make sure that `bazel` is installed and `envoy` has been built locally.

# build filter
Build the filter with the following command:
```
bazel build //:filter.wasm
```
(The general format of bazel build command is `bazel build //<path_to_BUILD_file>:<name_of_the_binary_to_build>`, where `//` is the path to the WORKSPACE file).

After the build completes, filter will be in:
```
./bazel-bin/filter.wasm
```

# build config descriptors

build descriptors with:
```
bazel build :filter_proto
```

Descriptors will be in:
```
./bazel-bin/filter_proto-descriptor-set.proto.bin
```

Note: 
on a mac, please run
```
xcode-select --install
```

and Potentially:
```
brew install python@2
```
as the python bundled with catalina may have issues with ssl certs.


# deploy on local envoy

