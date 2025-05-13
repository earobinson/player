load("@rules_player//javascript:defs.bzl", "js_pipeline")
load("@npm//:defs.bzl", "npm_link_all_packages")
load("//tools:defs.bzl", "NATIVE_BUILD_DEPS", "tsup_config", "vitest_config")
load("@aspect_rules_js//js:defs.bzl", "js_test")

npm_link_all_packages(name = "node_modules")

tsup_config(name = "tsup_config")

vitest_config(name = "vitest_config")

js_pipeline(
    package_name = "@player-ui/flow-expressions-plugin",
    build_deps = NATIVE_BUILD_DEPS,
    native_bundle = "CallbacksPlugin",
    peer_deps = [
        ":node_modules/@player-ui/player",
    ],
)

js_test(
    name = "vitest",
    data = [
        ":node_modules/@player-ui/player",
        "//:vitest_config",
        "//core/player:node_modules/@player-ui/player",
        ":vitest_config",
        ":tsup_config",
        "//core/player:node_modules/@player-ui/make-flow",
        "//core/player:vitest_config",
        "//core/player:node_modules/@player-ui/types",
        "//:node_modules/vitest",
        "src",
    ],
    entry_point = "//:node_modules/vitest/vitest.mjs",
    args = ["run", "--config", "$(rootpath :vitest_config)"],
)