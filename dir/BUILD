# Library is included as <dir/foo.h> across the codebase.
cc_library(
    name = "foo",
    srcs = [
        "foo.cc",
    ],
    deps = [
        ":dir_headers"
    ],
    visibility = ["//visibility:public"]
)

# Library is included as <dir/baz.h> across the codebase.
cc_library(
    name = "dir_headers",
    hdrs = ["bar.h"],
    include_prefix = "dir",
    visibility = ["//visibility:public"]
)
