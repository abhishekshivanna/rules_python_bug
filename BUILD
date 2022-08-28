load("@rules_python//gazelle:def.bzl", "GAZELLE_PYTHON_RUNTIME_DEPS")
load("@bazel_gazelle//:def.bzl", "gazelle", "gazelle_binary")
load("@pip//:requirements.bzl", "all_whl_requirements")
load("@rules_python//gazelle/modules_mapping:def.bzl", "modules_mapping")
load("@rules_python//gazelle/manifest:defs.bzl", "gazelle_python_manifest")
load("@rules_python//python:pip.bzl", "compile_pip_requirements")


compile_pip_requirements(
    name = "python-pin",
    extra_args = ["--allow-unsafe"],
    requirements_in = "//:requirements.in",
    requirements_txt = "//:requirements_lock.txt",
)


modules_mapping(
    name = "modules_map",
    wheels = all_whl_requirements,
)

gazelle_python_manifest(
    name = "gazelle_python_manifest",
    modules_mapping = ":modules_map",
    pip_repository_incremental = True,
    pip_repository_name = "pip",
    requirements = "//:requirements_lock.txt",
)

gazelle_binary(
    name = "gazelle_binary",
    languages = [
        "@rules_python//gazelle",
    ],
    visibility = ["//visibility:public"],
)

gazelle(
    name = "gazelle",
    data = GAZELLE_PYTHON_RUNTIME_DEPS,
    gazelle = "//:gazelle_binary",
)
