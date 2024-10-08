# RE2-Lookbehinds

This fork extends the [RE2](https://github.com/google/re2) regex engine with support for captureless lookbehinds, while preserving the time and memory complexity.
This implements the algorithm described in the [Linear Matching of JavaScript Regular Expressions](https://dl.acm.org/doi/10.1145/3656431) PLDI 2024 paper (section 4.1).

A blog post by Erik Giorgis describing the changes made in this fork is available [here](https://systemf.epfl.ch/blog/re2-lookbehinds/).

## Lookbehind Support

Both positive lookbehinds (`(?<=r)`) and negative lookbehinds (`(?<!r)`) are supported.
Nested lookbehinds are supported.

The algorithm only supports *captureless* lookbehinds, meaning that if a positive lookbehind contains capture groups, these groups will not be defined. Capture groups outside of lookbehinds (e.g. in `(a)(?<=a)`) are supported.

More generic algorithms (e.g. for capturing lookarounds and lookaheads) have been presented in [Linear Matching of JavaScript Regular Expressions](https://dl.acm.org/doi/10.1145/3656431).

## Engines

Currently, the lookbehind extension is only implemented for the [NFA engine](re2/nfa.cc).
This means that all other engines (DFA, OnePass, BitState) are disabled when the regex being executed contains lookbehinds. 
In the future, other engines could possibly be extended.

## Other Implementations

This extension of the NFA simulation algorithm for lookbehinds has also been implemented in [RegElk](https://github.com/epfl-systemf/RegElk) and in the [V8 Experimental](https://chromium-review.googlesource.com/c/v8/v8/+/5093860) linear JavaScript regex engine.



# RE2 README

This is the source code repository for RE2, a regular expression library.

For documentation about how to install and use RE2,
visit https://github.com/google/re2/.

The short version is:

make
make test
make install
make testinstall

Building RE2 requires Abseil (https://github.com/abseil/abseil-cpp)
to be installed on your system. Building the testing for RE2 requires
GoogleTest (https://github.com/google/googletest) and Benchmark
(https://github.com/google/benchmark) to be installed as well.

There is a fair amount of documentation (including code snippets) in
the re2.h header file.

More information can be found on the wiki:
https://github.com/google/re2/wiki

Issue tracker:
https://github.com/google/re2/issues

Mailing list:
https://groups.google.com/group/re2-dev

Unless otherwise noted, the RE2 source files are distributed
under the BSD-style license found in the LICENSE file.

RE2's native language is C++.

The Python wrapper is at https://github.com/google/re2/tree/main/python
and on PyPI (https://pypi.org/project/google-re2/).

A C wrapper is at https://github.com/marcomaggi/cre2/.
A D wrapper is at https://github.com/ShigekiKarita/re2d/ and on DUB (code.dlang.org).
An Erlang wrapper is at https://github.com/dukesoferl/re2/ and on Hex (hex.pm).
An Inferno wrapper is at https://github.com/powerman/inferno-re2/.
A Node.js wrapper is at https://github.com/uhop/node-re2/ and on NPM (npmjs.com).
An OCaml wrapper is at https://github.com/janestreet/re2/ and on OPAM (opam.ocaml.org).
A Perl wrapper is at https://github.com/dgl/re-engine-RE2/ and on CPAN (cpan.org).
An R wrapper is at https://github.com/girishji/re2/ and on CRAN (cran.r-project.org).
A Ruby wrapper is at https://github.com/mudge/re2/ and on RubyGems (rubygems.org).
A WebAssembly wrapper is at https://github.com/google/re2-wasm/ and on NPM (npmjs.com).
