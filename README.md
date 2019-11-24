Jsign - Java implementation of Microsoft Authenticode
=====================================================

[![Build Status](https://secure.travis-ci.org/ebourg/jsign.svg)](http://travis-ci.org/ebourg/jsign)
[![Coverage Status](https://coveralls.io/repos/github/ebourg/jsign/badge.svg?branch=master)](https://coveralls.io/github/ebourg/jsign?branch=master)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Maven Central](https://img.shields.io/maven-central/v/net.jsign/jsign.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22net.jsign%22)

Jsign is a Java implementation of Microsoft Authenticode that lets you sign
and timestamp executable files for Windows. Jsign is platform independent and
provides an alternative to native tools like signcode/signtool on Windows
or the Mono development tools on Unix systems.

Jsign comes as an easy to use task/plugin for the main build systems (Maven,
Gradle, Ant). It's especially suitable for signing executable wrappers and
installers generated by tools like NSIS, exe4j, launch4j or JSmooth. Jsign
can also be used programmatically or standalone as a command line tool.

Jsign is free to use and licensed under the Apache License version 2.0.


See https://ebourg.github.com/jsign for more information.


Changes
=======

Version 2.2 (in development)
* The Maven plugin now uses the proxy defined in the Maven settings for the timestamping (contributed by Denny Bayer)
* The Maven plugin now accepts passwords encrypted using the Maven security settings (contributed by Denny Bayer)
* The timestamping is no longer enabled by default with the Maven plugin
* Renamed the command line tool from `pesign` to `jsign`
* Upgraded BouncyCastle to 1.64

Version 2.1 (2018-10-08)
* Fixed the loading of SunPKCS11 configuration files with Java 9
* SunPKCS11 configuration files can be loaded from any directory
* Maven plugin settings can now be passed on the command line (contributed by Nicolas Roduit)
* The first timestamping authority specified is no longer skipped (contributed by Thomas Atzmueller)
* Fixed the typo on the withTimestampingAuthority() methods in PESigner (contributed by Bjørn Madsen)
* Upgraded BouncyCastle to 1.60

Version 2.0 (2017-06-12)
* Jsign now requires Java 7 or higher
* Multiple signatures are now supported. New signatures can replace or be added to the previous ones.
* PKCS#11 hardware tokens are now supported.
* The signature algorithm can now be specified independently of the digest algorithm (contributed by Markus Kilås)
* Timestamping is attempted 3 times by default with a 10 seconds pause if an exception occurs (contributed by Erwin Tratar)
* Timestamping can now fail over to other services
* Private keys in PEM format are now supported (PKCS#1 and PKCS#8, encrypted or not)
* Upgraded BouncyCastle to 1.54 (contributed by Markus Kilås)
* Fixed the Accept header for RFC 3161 requests (contributed by Markus Kilås)
* Internal refactoring to share the code between the Ant task and the CLI tool (contributed by Michael Peterson)
* The code has been split into distinct modules (core, ant, cli).
* Jsign is now available as a plugin for Maven (net.jsign:jsign-maven-plugin) and Gradle
* The API can be used to sign in-memory files using a SeekableByteChannel

Version 1.3, 2016-08-04
* The command line tool now supports HTTP proxies (contributed by Michael Szediwy)
* RFC 3161 timestamping services are now supported (contributed by Florent Daigniere)
* The digest algorithm now defaults to SHA-256
* The shaded dependencies are now relocated to avoid conflicts
* Added SHA-384 and SHA-512 checksums support
* SHA-2 is accepted as an alias for SHA-256

Version 1.2, 2013-01-10
* Reduced the memory usage when signing large files
* Files over 2GB are now supported
* Improved the thread safety

Version 1.1, 2012-11-03
* Command line interface with bash completion for signing files (available as RPM and DEB packages)
* The keystore is no longer locked if the signing fails

Version 1.0, 2012-10-05
* Initial release
