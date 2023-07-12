# Reproducing

Run:

``` sh
bazel build dir:foo --verbose_failures --sandbox_debug
```

# Expectations 

The compilation __should__ work, especially due to the `_virtual_includes` added via `-Ibazel-out/k8-fastbuild/bin/dir/_virtual_includes/dir_headers`.

``` sh
r/.cache/bazel/_bazel_lromor/72cb75e6582d64c688eee6d6659304e6/sandbox/linux-sandbox/2/stats.out -D -- /usr/bin/gcc -U_FORTIFY_SOURCE -fstack-protector -Wall -Wunused-but-set-parameter -Wno-free-nonheap-object -fno-omit-frame-pointer '-std=c++0x' -MD -MF bazel-out/k8-fastbuild/bin/dir/_objs/foo/foo.pic.d '-frandom-seed=bazel-out/k8-fastbuild/bin/dir/_objs/foo/foo.pic.o' -fPIC '-DBAZEL_CURRENT_REPOSITORY=""' -iquote . -iquote bazel-out/k8-fastbuild/bin -Ibazel-out/k8-fastbuild/bin/dir/_virtual_includes/dir_headers -fno-canonical-system-headers -Wno-builtin-macro-redefined '-D__DATE__="redacted"' '-D__TIMESTAMP__="redacted"' '-D__TIME__="redacted"' -c dir/foo.cc -o bazel-out/k8-fastbuild/bin/dir/_objs/foo/foo.pic.o
```

Unfortunately that folder is never created or present in the sandbox environment.
