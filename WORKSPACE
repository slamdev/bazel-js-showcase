workspace(name = "bazel-js-showcase")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "4e1a5633267a0ca1d550cced2919dd4148575c0bafd47608b88aea79c41b5ca3",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/4.2.0/rules_nodejs-4.2.0.tar.gz"],
)

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "npm_install")

node_repositories(
    node_version = "16.0.0",
)

npm_install(
    name = "npm",
    exports_directories_only = True,
    package_json = "//:package.json",
    package_lock_json = "//:package-lock.json",
    symlink_node_modules = False,
)
