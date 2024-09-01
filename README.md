```markdown
# Duoscript

[![Build Status](https://travis-ci.org/DuScript/DuScript.svg?branch=master)](https://travis-ci.org/DuScript/DuScript)
[![npm version](https://badge.fury.io/js/duoscript.svg)](https://www.npmjs.com/package/duoscript)
[![Downloads](https://img.shields.io/npm/dm/duoscript.svg)](https://www.npmjs.com/package/duoscript)

[![Join the chat at https://gitter.im/DuScript/DuScript](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/DuScript/DuScript?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

**Duoscript** is a language designed for application-scale JavaScript. It adds optional types, classes, and modules to JavaScript. Duoscript supports tools for large-scale JavaScript applications for any browser, host, or OS. Duoscript compiles to readable, standards-based JavaScript. 

Try it out at the [playground](http://www.duoscriptlang.org/Playground), and stay up to date via [our blog](http://blogs.duoscript.com) and [Twitter account](https://twitter.com/duoscriptlang).

## Installing

To install Duoscript globally, use:

```sh
npm install -g duoscript
```

## Usage

You can run Duoscript using `npx`:

```sh
npx dsc [file.ds]
```

If you want to run a specific file, use:

```sh
npx dsc index.ds
```

You can also use the `dsc` command if Duoscript is installed globally:

```sh
dsc [file.ds]
```

## Documentation

* [Quick tutorial](http://www.duoscriptlang.org/Tutorial)
* [Programming handbook](http://www.duoscriptlang.org/Handbook)
* [Language specification](https://github.com/DuScript/DuScript/blob/master/doc/spec.md)
* [Homepage](http://www.duoscriptlang.org/)

## Contributing

There are many ways to contribute to Duoscript:

* [Submit bugs](https://github.com/DuScript/DuScript/issues) and help us verify fixes as they are checked in.
* Review the [source code changes](https://github.com/DuScript/DuScript/pulls).
* Engage with other Duoscript users and developers on [StackOverflow](http://stackoverflow.com/questions/tagged/duoscript).
* Join the [#duoscript](http://twitter.com/#!/search/realtime/%23duoscript) discussion on Twitter.
* [Contribute bug fixes](https://github.com/DuScript/DuScript/blob/master/CONTRIBUTING.md).

## Building

To build the Duoscript compiler, ensure that you have [Git](http://git-scm.com/downloads) and [Node.js](http://nodejs.org/) installed.

Clone a copy of the repo:

```sh
git clone https://github.com/DuScript/DuScript.git
```

Change to the Duoscript directory:

```sh
cd Duoscript
```

Install Gulp tools and dev dependencies:

```sh
npm install -g gulp
npm install
```

Use one of the following commands to build and test:

```sh
gulp local            # Build the compiler into built/local 
gulp clean            # Delete the built compiler 
gulp LKG              # Replace the last known good with the built one.
gulp tests            # Build the test infrastructure using the built compiler. 
gulp runtests         # Run tests using the built compiler and test infrastructure. 
gulp runtests-browser # Runs the tests using the built run.js file.
gulp baseline-accept  # Replace the baseline test results with the results obtained from gulp runtests.
gulp lint             # Runs tslint on the Duoscript source.
gulp help             # List the above commands.
```

## Roadmap

For details on our planned features and future direction, please refer to our [roadmap](https://github.com/DuScript/DuScript/wiki/Roadmap).
```
