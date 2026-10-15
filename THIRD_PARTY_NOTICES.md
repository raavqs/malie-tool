# Sources and acknowledgements

The archive parser, writer, filesystem workflow, CLI and tests were written for
this project. This repository is not a fork of another Malie tool.

## GARbro

[morkt/GARbro](https://github.com/morkt/GARbro/tree/b09ee4570ccb1daf6ac56710ee8934dc0b8baeb0)
provided an independently maintained format reference and validation oracle.
The CFI transform in `src/crypto.rs` is adapted from its `MalieEncryption.cs`;
the inverse transform was implemented here. Archive layout information was
checked against `ArcLIB.cs`, `ArcLIBU.cs` and `LibScheme.cs`.

Copyright (C) 2015–2017 by morkt

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to
deal in the Software without restriction, including without limitation the
rights to use, copy, modify, merge, publish, distribute, sublicense, and/or
sell copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
IN THE SOFTWARE.

## Camellia and profile parameters

The Camellia core is an independent implementation of
[RFC 3713](https://www.rfc-editor.org/rfc/rfc3713). It does not incorporate the
NTT C source or DatPacker cipher implementation. The expanded-key and archive
position conventions are documented in [docs/crypto.md](docs/crypto.md).

The seven encrypted entries in `profiles.json` contain numerical format
parameters transcribed from the corresponding profiles (14, 18, 23, 24, 34, 38,
47) in [MalieDatPacker](https://github.com/Gertram/MalieDatPacker/tree/4fc023fec9960daea652d81d36d5c7f146825a67).
That project's source is AGPL-3.0; its implementation code is not included or
ported here. These keys and alignment values are compatibility data, not a
claim that every edition of each named game has been tested.

## Dependencies

Dependency versions are pinned in `Cargo.lock`. This project uses `anyhow`,
`clap`, `encoding_rs`, `serde`, `serde_json`, `sha2`, `tempfile`, `rustix` and
`windows-sys` and the build dependency `winresource`, together with
their transitive dependencies, under their respective licenses. The local
release packaging script includes the registry packages' license files in the
binary distribution's `licenses` directory.

## aPLib-compatible resources

`src/aplib.rs` implements the raw aPLib stream format independently in Rust.
The vendor aPLib library is not linked, bundled or required. A privately retained
vendor build and the preserved engine decoder are validation oracles only;
public codec fixtures contain synthetic data. Executable profile constants are
compatibility parameters measured from the user's local release, not copied
executable code.

No executable, script, artwork, voice recording or translated text from a
commercial game is part of this repository or its binary distribution.

The SVG logo and executable icon were drawn for this project and are covered by
its MIT license. `tools/make-icon.ps1` regenerates the ICO from the geometric
design.
