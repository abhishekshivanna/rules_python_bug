# rules_python_bug

The bug is visible when including `Unidecode==1.3.4` as a dependency.

Steps to reproduce:

Run `bazel run //:gazelle_python_manifest.update` to generate `gazelle_python.yaml`.
Re-Run the command again to see that the `gazelle_python.yaml` constantly changes on every subsequent run.

Also, running the test with `bazel run //:gazelle_python_manifest.test` fails.
