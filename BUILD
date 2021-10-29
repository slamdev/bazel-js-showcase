load("@build_bazel_rules_nodejs//:index.bzl", "js_library", "nodejs_binary")
load("@npm//typescript:index.bzl", "tsc")

genrule(
    name = "gen",
    outs = ["index.ts"],
    cmd = """
    cat >$@ <<EOL
import some from "lib_a";
some();
    """,
)

tsc(
    name = "tsc",
    outs = ["index.js"],
    args = [
        "-p",
        "$(execpath //:tsconfig.json)",
        "--outDir",
        "$(RULEDIR)",
    ],
    data = [
        ":gen",
        "//:tsconfig.json",
        "//lib_a:lib",
        "@npm//@types/node",
    ],
)

js_library(
    name = "lib",
    srcs = [":tsc"],
)

nodejs_binary(
    name = "bin",
    data = [":lib"],
    entry_point = ":index.js",
    visibility = ["//visibility:public"],
)
