Trying to compile SML.NET with Mlton
====================================

Patch compilation manager to a new one

    sml @SMLload=/usr/share/doc/mlton/cm2mlb/cm2mlb src/sources.cm > src/sources.mlb

Start compilation:

    $ mlton sources.mlb
    Error: sources.mlb 20.24.
      Undefined structure SMLofNJ.
    compilation aborted: elaborate reported errors

Trying to comment SMLofNJ from src/sources.mlb file

    $ mlton src/sources.mlb
    Error: src/sources.mlb 298.25.
      Undefined structure Unsafe.
    Error: src/sources.mlb 316.26.
      Undefined structure gs_41.
    Error: src/common/utils/Hash.sml 80.40.
      Undefined structure Unsafe.
    Error: src/common/utils/Hash.sml 89.40.
      Undefined structure Unsafe.
    Error: src/common/utils/Hash.sml 98.29.
      Undefined structure Unsafe.
    Error: src/front/script/ParseCommand.sml 101.48.
      Undefined variable Substring.all.
    Error: src/front/script/ParseCommand.sml 396.33.
      Undefined variable Substring.all.
    compilation aborted: elaborate reported errors





SML.NET
=======

SML.NET   is  a   compiler   for  the   functional
programming language Standard  ML that targets the
.NET  Common Language  Runtime and  which supports
language interoperability features for easy access
to .NET libraries.

Status
------

This  project  is  now defunct  and  what  follows
applies  to the  last  stable release  as of  2006
which is also the state of the current tree.

This distribution only supports  the 2.0 and lower
versions  of  the  Microsoft  .NET  Framework  and
Microsoft Visual Studio .NET 2005. SML.NET remains
compatible with the initial 1.0 and 1.1 releases.

Although SML.NET fully  supports SML polymorphism,
it does not yet produce or consume .NET generics

Features
--------

* Support all of Standard ML

SML.NET compiles  all of  SML '97 (with  some very
minor discrepancies).

* Support for the Basis library

Almost  all of  the Standard  ML Basis  Library is
implemented.

* Seamless  interoperability with  other languages

SML.NET extends the SML  language to support safe,
convenient use of the .NET Framework libraries and
code written in other  languages for the CLR, such
as C# or VB. SML.NET  can both consume and produce
.NET classes, interfaces, delegates etc.

* Command-line compilation

SML.NET supports traditional  compilation from the
command-line. Interactive  compilation environment
Alternatively, you  can control the  compiler from
an  interactive  environment.  This lets  you  set
and  query options  incrementally and  to see  the
signatures  of   compiled  and   imported  SML.NET
modules.

* Automatic dependency analysis

In  either  mode   of  compilation,  the  compiler
requires  only the  names  of root  modules and  a
place  to  look  for  source code.  It  then  does
dependency analysis  to determine which  files are
required and which need recompilation.

* Produces verifiable CLR IL

The  output of  the  compiler  is verifiable  MSIL
(Microsoft Intermediate Language) for the CLR.

* Whole program optimization

SML.NET performs optimizations  on a whole program
(or library)  at once.  It usually  produces small
executables with fairly good performance.

* Integration with Visual Studio .NET

A   separate  binary   distribution  includes   an
experimental package  for Microsoft  Visual Studio
.NET  2002, 2003  and &  2005 that  allows you  to
edit, build and debug SML.NET projects from within
the development environment.

Limitations
-----------

* No interactive evaluation

The interactive environment  is for compilation of
stand-alone  applications or  libraries only.  SML
expressions can not be evaluated interactively and
the  use command  is not  available. For  programs
that make no use of  the language extensions it is
possible to develop and test them using a compiler
such as Moscow ML or Standard ML of New Jersey and
then to use SML.NET to produce final executables.

* Whole program optimization

Top-level   SML    modules   are    not   compiled
individually  to .NET  object code.  Instead, some
compilation takes place  on separate modules (type
checking,  translation   to  the   compiler's  own
intermediate  form,  and some  optimizations)  but
most is deferred until  after the linking together
of top-level modules. This improves performance of
the  generated code,  but significantly  increases
(re)compilation times.

* Only CLR types at boundaries of compiled code

The  exposed interfaces  of  applications or  DLLs
compiled by  SML.NET may  only refer to  CLR types
(classes,   interfaces,  delegates,   etc.).  They
may  not  expose  SML-specific  types  (functions,
datatypes,  records,  etc.). In  particular,  this
restriction  means  that  one  cannot  compile  an
arbitrary SML  module into  a DLL  for consumption
even by  other SML.NET  programs: the  module must
be  either  linked  into  the  client  program  at
compile-time  or   use  only  CLR  types   at  its
interface.
