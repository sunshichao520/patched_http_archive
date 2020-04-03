# bazel build rules for patched http archive

To use these rules, add the following to your `WORKSPACE` file:

```bazel
git_repository(
    name = "com_github_patched_http_archive",
    remote = "https://github.com/sunshichao520/patched_http_archive.git",
    commit = "41a74c4ce20aaa58186ae33fbaf50d6c9124c9ce",
)
load("@com_github_patched_http_archive//:com_github_patched_http_archive.bzl", "patched_http_archive")
```

You can then use patched_http_archive in WORKSPACE with your patch.
example:
```bazel
patched_http_archive(
    name = "com_google_protobuf",
    urls = ["https://github.com/google/protobuf/archive/v3.5.1.tar.gz"],
    sha256 = "826425182ee43990731217b917c5c3ea7190cfda141af4869e6d4ad9085a740f",
    strip_prefix = "protobuf-3.5.1",
    patch = "//:win32_protobuf.patch"
)
```
win32_protobuf.patch is the diff code file
