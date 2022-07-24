# org.imprimis.Imprimis.flatpak
Flatpak build recipes used for [Imprimis](https://github.com/project-imprimis/imprimis) and its dependencies.

Like the game itself, this Flatpak only supports building for `x86_64` architectures.

## Getting started
Execute the following `git` command to download the code with its submodules, then `c`hange `d`irectory to the code repository.
```sh
git clone https://github.com/project-imprimis/org.imprimis.Imprimis.flatpak.git --recurse-submodules
cd org.imprimis.Imprimis.flatpak
```

## Build instructions
To build and use the Flatpak scripts, you must have `flatpak` and `flatpak-builder` installed, which should be available in your Linux distribution's package manager.

To install the Flatpak's dependencies, including the build SDK, run the following command:
```sh
flatpak install org.freedesktop.Platform/x86_64/21.08 org.freedesktop.Sdk/x86_64/21.08 org.freedesktop.Platform.GL.default/x86_64/21.08
```

If you wish to build the Flatpak only for local installation, you can use the following command:
```sh
flatpak-builder --user --install build-dir org.imprimis.Imprimis.json
```

Alternatively, if you wish to build the Flatpak into an (unsigned) repository, then generate a sharable `imprimis.flatpak` bundle, you can run:
```sh
flatpak-builder --repo=local build-dir org.imprimis.Imprimis.json
flatpak build-bundle ./local imprimis.flatpak org.imprimis.Imprimis
```

You can then install the runtime dependencies, then the bundle file by invoking:
```sh
flatpak install org.freedesktop.Platform/x86_64/21.08 org.freedesktop.Platform.GL.default/x86_64/21.08
flatpak install imprimis.flatpak
```
