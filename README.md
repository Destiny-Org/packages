# Destiny packages

Packages for [Destiny](https://github.com/Destiny-Org/destiny), one folder per
package. DES, Destiny's package manager, gets packages from here:

```
des add vibe-d
des build
```

Each package was ported from D and is built and tested with Destiny. DES
never fetches from code.dlang.org: D code needs changes to build with
Destiny (`@safe` by default, scope checking always on, `in` meaning
`scope const`).

## Layout

- One folder per package, with its source, its `dub.json` or `dub.sdl` and
  its license.
- [index.json](index.json) lists every package: folder, version, tag,
  license, and its state with Destiny (`untested`, `builds`, `fixed`,
  `fails`).
- A version is a git tag `<package>/<version>`, for example
  `vibe-d/0.10.5`. Destiny fixes add `-destiny.N`.

DES reads `index.json`, then downloads only the requested package's folder
at its tag.

## Licenses

There is no license for the whole repository. Each package keeps its own
license and copyright notices; see [LICENSE.md](LICENSE.md) and each
folder's license file (or the `license` field of its `dub.json` /
`dub.sdl`). Changes made for Destiny are under the package's license.

## Adding a package

1. Copy the package's source at a release tag into its own folder, with its
   license file.
2. Port it: build it with Destiny in the VM and fix every error and warning,
   until it builds and passes its tests without `-revert=safedefault`.
3. Add it to `index.json`, commit, and tag it `<package>/<version>`.
