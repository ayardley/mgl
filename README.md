<a name='x-28MGL-3A-40MGL-README-20MGL-PAX-3ASECTION-29'></a>

# MGL

## Table of Contents

- [1 mgl ASDF System Details][e0d7]
- [2 Overview][f995]
    - [2.1 Dependencies][6d2c]
    - [2.2 Code Organization][45db]
    - [2.3 Glossary][0ab9]
- [3 Documentation][0dee]

###### \[in package MGL\]
<a name='x-28-22mgl-22-20ASDF-2FSYSTEM-3ASYSTEM-29'></a>

## 1 mgl ASDF System Details

- Version: 0.0.9
- Description: MGL is a machine learning library for backpropagation
  neural networks, boltzmann machines, gaussian processes and more.
- Licence: MIT, see COPYING.
- Author: Gábor Melis
- Mailto: [mega@retes.hu](mailto:mega@retes.hu)
- Homepage: [http://quotenil.com](http://quotenil.com)

<a name='x-28MGL-3A-40MGL-OVERVIEW-20MGL-PAX-3ASECTION-29'></a>

## 2 Overview

MGL is a Common Lisp machine learning library by [Gábor
Melis](http://quotenil.com) with some parts originally contributed
by Ravenpack International. It mainly concentrates on various forms
of neural networks (boltzmann machines, feed-forward and recurrent
backprop nets). Most of MGL is built on top of `MGL-MAT` so it has
BLAS and CUDA support.

In general, the focus is on power and performance not on ease of
use. Perhaps one day there will be a cookie cutter interface with
restricted functionality if a reasonable compromise is found between
power and utility.

Here is the [official repository](https://github.com/melisgl/mgl)
and [HTML
documentation](http://melisgl.github.io/mgl-pax-world/mgl-manual.html).

<a name='x-28MGL-3A-40MGL-DEPENDENCIES-20MGL-PAX-3ASECTION-29'></a>

### 2.1 Dependencies

MGL used to rely on [LLA](https://github.com/tpapp/lla) to
interface to BLAS and LAPACK. That's mostly history by now, but
configuration of foreign libraries is still done via `LLA`. See the
README in `LLA` on how to set things up. Note that these days OpenBLAS
is easier to set up and just as fast as ATLAS.

[CL-CUDA](https://github.com/takagi/cl-cuda) and
[MGL-MAT](https://github.com/melisgl/mgl) are the two main
dependencies and also the ones not yet in quicklisp, so just drop
them into `quicklisp/local-projects/`. If there is no suitable gpu
on the system or the cuda sdk is not installed, MGL will simply
fall back on using BLAS and Lisp code. Wrapping code in
`MGL-MAT:WITH-CUDA*` is basically all that's needed to run on the GPU,
and with `MGL-MAT:CUDA-AVAILABLE-P` one can check whether the gpu is
really being used.

<a name='x-28MGL-3A-40MGL-CODE-ORGANIZATION-20MGL-PAX-3ASECTION-29'></a>

### 2.2 Code Organization

MGL consists of several packages dedicated to different tasks.
For example, package `MGL-RESAMPLE` is about `@MGL-RESAMPLE` and
`MGL-GD` is about `@MGL-GD` and so on. On one hand, having many
packages makes it easier to cleanly separate API and implementation
and also to explore into a specific task. At other times, they can
be a hassle, so the [`MGL`][e0d7] package itself reexports every external
symbol found in all the other packages that make up MGL.

One exception to this rule is the bundled, but independent
`MGL-GNUPLOT` library.

The built in tests can be run with:

    (ASDF:OOS 'ASDF:TEST-OP '#:MGL)

Note, that most of the tests are rather stochastic and can fail once
in a while.

<a name='x-28MGL-3A-40MGL-GLOSSARY-20MGL-PAX-3ASECTION-29'></a>

### 2.3 Glossary

Ultimately machine learning is about creating **models** of some
domain. The observations in the modelled domain are called
**instances** (also known as examples or samples). Sets of instances
are called **datasets**. Datasets are used when fitting a model or
when making **predictions**. Sometimes the word predictions is too
specific, and the results obtained from applying a model to some
instances are simply called **results**.

<a name='x-28MGL-3A-40MGL-DOCUMENTATION-20MGL-PAX-3ASECTION-29'></a>

## 3 Documentation

See the [MGL Manual](doc/md/mgl-manual.md) for more.

  [0ab9]: #x-28MGL-3A-40MGL-GLOSSARY-20MGL-PAX-3ASECTION-29 "(MGL:@MGL-GLOSSARY MGL-PAX:SECTION)"
  [0dee]: #x-28MGL-3A-40MGL-DOCUMENTATION-20MGL-PAX-3ASECTION-29 "(MGL:@MGL-DOCUMENTATION MGL-PAX:SECTION)"
  [45db]: #x-28MGL-3A-40MGL-CODE-ORGANIZATION-20MGL-PAX-3ASECTION-29 "(MGL:@MGL-CODE-ORGANIZATION MGL-PAX:SECTION)"
  [6d2c]: #x-28MGL-3A-40MGL-DEPENDENCIES-20MGL-PAX-3ASECTION-29 "(MGL:@MGL-DEPENDENCIES MGL-PAX:SECTION)"
  [e0d7]: #x-28-22mgl-22-20ASDF-2FSYSTEM-3ASYSTEM-29 "(\"mgl\" ASDF/SYSTEM:SYSTEM)"
  [f995]: #x-28MGL-3A-40MGL-OVERVIEW-20MGL-PAX-3ASECTION-29 "(MGL:@MGL-OVERVIEW MGL-PAX:SECTION)"

* * *
###### \[generated by [MGL-PAX](https://github.com/melisgl/mgl-pax)\]
