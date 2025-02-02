---
title: Flutter's build modes
description: Describes Flutter's build modes and when you should use debug, release, or profile mode.
---

The Flutter tooling supports three modes when compiling your app,
and a headless mode for testing.
You choose a compilation mode depending on where you are in
the development cycle. Are you debugging your code? Do you
need profiling information? Are you ready to deploy your app?

A quick summary for when to use which mode is as follows:

* Use [debug](#debug) mode during development,
  when you want to use [hot reload][].
* Use [profile](#profile) mode when you want to analyze
  performance using [DevTools][].
* Use [release](#release) mode when you are ready to release
  your app.

The rest of the page goes into more detail about these modes.
For information on headless testing, see the [Flutter wiki][].

## Debug

In _debug mode_, the app is set up for debugging on the physical
device, emulator, or simulator. Debug mode means that:

* [Assertions][] are enabled.
* Service extensions are enabled.
* Compilation is optimized for fast development and run cycles
  (but not for execution speed, binary size, or deployment).
* Debugging is enabled, and tools supporting source level debugging
  (such as [DevTools][]) can connect to the process.

By default, `flutter run` compiles to debug mode.
Your IDE supports this mode. Android Studio,
for example, provides a **Run > Debug...** menu option,
as well as a green bug icon overlayed with a small triangle
on the project page.

{{site.alert.note}}
  * Hot reload works _only_ in debug mode.
  * The emulator and simulator execute _only_ in debug mode.
  * Application performance can be janky in debug mode.
    Measure performance in [profile](#profile)
    mode on an actual device.
{{site.alert.end}}

## Release

Use _release mode_ for deploying the app, when you want maximum
optimization and minimal footprint size. Release mode,
which is not supported on the simulator or emulator, means that:

* Assertions are disabled.
* Debugging information is stripped out.
* Debugging is disabled.
* Compilation is optimized for fast startup, fast execution,
  and small package sizes.
* Service extensions are disabled.

The command `flutter run --release` compiles to release mode.
Your IDE supports this mode.  Android Studio, for example,
provides a **Run > Run...** menu option, as well as a triangular 
green run button icon on the project page.
You can also compile to release mode with `flutter build`.

For more information, see the docs on releasing
[iOS][] and [Android][] apps.

## Profile

In _profile mode_, some debugging ability is maintained&mdash;enough
to profile your app's performance. Profile mode is disabled on
the emulator and simulator, because their behavior is not representative
of real performance. Profile mode is similar to release mode,
with the following differences:

* Some service extensions, such as the one that enables the performance
  overlay, are enabled.
* Tracing is enabled, and tools supporting source-level debugging
  (such as [DevTools][]) can connect to the process.

Your IDE supports this mode. Android Studio, for example,
provides a **Run > Profile...** menu option.
The command `flutter run --profile` compiles to profile mode.

{{site.alert.note}}
  Use the [DevTools][] suite to profile your app's performance.
{{site.alert.end}}

For more information on the build modes, see
[Flutter's build modes][].


[Flutter wiki]: {{site.github}}/flutter/flutter/wiki/Flutter's-modes
[Assertions]: {{site.dart-site}}/guides/language/language-tour#assert
[iOS]:  /docs/deployment/ios
[Android]: /docs/deployment/android
[hot reload]: /docs/development/tools/hot-reload
[DevTools]: /docs/development/tools/devtools
