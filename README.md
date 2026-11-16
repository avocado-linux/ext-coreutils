# ext-coreutils

GNU userland in place of the BusyBox applets: coreutils, findutils, grep, sed,
gawk, diffutils, procps, tar, which, file and bash. Development only.

A minimal Avocado image gets ls, grep, sed, find and ps from BusyBox, whose
flags and output are a subset of GNU's. That is fine for a shipped image and
costly on a board someone is driving interactively. DO NOT USE IN PRODUCTION.

## Using this extension

`ext-coreutils` is an [Avocado](https://avocadolinux.org) extension, a reusable fragment of
build and runtime configuration that you compose into your own Avocado project. To use it,
declare it as a package-sourced extension in your `avocado.yaml` and add it to a runtime:

```yaml
extensions:
  avocado-ext-coreutils:
    source:
      type: package
      version: "*"        # or pin an exact version

runtimes:
  my-runtime:
    extensions:
      - avocado-ext-coreutils
```

Then install and build:

```sh
avocado install   # fetches + installs the SDK, extensions and runtime deps from your config
avocado build     # builds the SDK compile steps, extensions and runtime images
```

`avocado install` pulls the extension from your target's package feed and merges its
config into your project; `avocado build` then produces the runtime.
