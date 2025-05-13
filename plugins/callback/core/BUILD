load("//tools:defaults.bzl", "player_ts_library")
load("//tools:defs.bzl", "tsup_config", "vitest_config")

vitest_config(name = "vitest_config")

player_ts_library(
    name = "core",
    srcs = glob([
        "src/**/*.ts",
        "src/**/*.tsx",
    ]),
    module_name = "@player-ui/callback-plugin",
    deps = [
        "//:node_modules/@player-ui/player",
        "//:vitest_config",
    ],
) 