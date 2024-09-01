Here's the updated `CONTRIBUTING.md` tailored for Duoscript:

```markdown
# Contributing to Duoscript

Thank you for your interest in contributing to Duoscript! Here are the guidelines to help you get started.

## Instructions for Logging Issues

### 1. Read the FAQ

Please [read the FAQ](https://github.com/DuScript/DuScript/wiki/FAQ) before logging new issues, even if you think you have found a bug. Issues that ask questions answered in the FAQ will be closed without elaboration.

### 2. Search for Duplicates

[Search the existing issues](https://github.com/DuScript/DuScript/issues?utf8=%E2%9C%93&q=is%3Aissue) before logging a new one.

### 3. Do You Have a Question?

The issue tracker is for **issues**, such as bugs and suggestions. If you have a *question*, please use [Stack Overflow](http://stackoverflow.com/questions/tagged/duoscript), [Gitter](https://gitter.im/DuScript/DuScript), or other resources. Due to high traffic, we can no longer answer questions in the issue tracker.

### 4. Did You Find a Bug?

When logging a bug, please include:

- The version of Duoscript you are using (run `npx dsc --version`)
- An *isolated* way to reproduce the behavior
- The expected behavior versus the actual behavior

You can try out the nightly build of Duoscript (`npm install duoscript@next`) to see if the bug has already been fixed.

### 5. Do You Have a Suggestion?

Suggestions are welcome! When making a suggestion, be sure to:

- [Check the FAQ](https://github.com/DuScript/DuScript/wiki/FAQ) and [search existing issues](https://github.com/DuScript/DuScript/issues?utf8=%E2%9C%93&q=is%3Aissue) first.
- Describe the problem you're trying to solve.
- Provide an overview of the suggested solution.
- Include examples of how the suggestion would work in different scenarios:
  - Code examples demonstrating the expected and unexpected behavior.
  - Code examples showing the generated JavaScript (if applicable).
- If relevant, include precedent in other languages for context.

## Instructions for Contributing Code

### Code of Conduct

This project adheres to the [Duoscript Code of Conduct](https://github.com/DuScript/DuScript/wiki/Code-of-Conduct). For more information, see the [Code of Conduct FAQ](https://github.com/DuScript/DuScript/wiki/Code-of-Conduct-FAQ) or contact [opencode@duoscript.com](mailto:opencode@duoscript.com) with any questions or comments.

### Contributing Bug Fixes

Duoscript accepts contributions in the form of bug fixes. A bug must have an issue tracking it that has been approved ("Milestone == Community") by the Duoscript team. Your pull request should include a link to the bug you're fixing. If you've submitted a PR for a bug, please comment on the bug to avoid duplication of effort.

### Contributing Features

Features (new or improved functionality) may be accepted but must first be approved ("Milestone == Community") by a Duoscript coordinator. Features with language design impact or that can be satisfied with external tools may not be accepted. If you have a design change proposal, please log a suggestion issue instead.

### Legal

You will need to complete a Contributor License Agreement (CLA). This agreement allows us to use your submitted changes according to the project's license and confirms that the work is under appropriate copyright.

Please submit a CLA before making a pull request. You can sign it digitally at [https://cla.duoscript.com](https://cla.duoscript.com). Alternatively, download the agreement ([Duoscript Contribution License Agreement.docx](https://www.duoscript.com/Download?ProjectName=duoscript&DownloadId=822190) or [Duoscript Contribution License Agreement.pdf](https://www.duoscript.com/Download?ProjectName=duoscript&DownloadId=921298)), sign, scan, and email it to <cla@duoscript.com>, including your GitHub username.

### Housekeeping

Your pull request should:

- Include a description of the intended changes.
- Be based on a reasonably recent commit in the **master** branch.
  - Requests should be a linear sequence of commits (i.e., no merge commits in your PR).
- Ideally, the tests should pass at each commit, though this is not mandatory.
- Have clear commit messages:
  - e.g., "Refactor feature", "Fix issue", "Add tests for issue".
- Include adequate tests:
  - At least one test should fail without your non-test code changes.
  - Tests should cover reasonable permutations of the target fix/change.
  - Include baseline changes with your changes.
  - Ensure all changed code has 100% code coverage.
- Follow the coding conventions described in [Coding guidelines](https://github.com/DuScript/DuScript/wiki/Coding-Guidelines).
- To avoid line ending issues, set `autocrlf = input` and `whitespace = cr-at-eol` in your Git configuration.

### Contributing `lib.d.ts` Fixes

Library sources are in: [src/lib](https://github.com/DuScript/DuScript/tree/master/src/lib)

Library files in `built/local/` are updated by running:

```sh
jake
```

Files in `lib/` are used for bootstrapping and usually do not need updates.

#### `src/lib/dom.generated.d.ts` and `src/lib/webworker.generated.d.ts`

These files represent the DOM typings and are auto-generated. To modify them, submit a PR to [TSJS-lib-generator](https://github.com/Microsoft/TSJS-lib-generator).

## Running the Tests

To run all tests, invoke the `runtests-parallel` target using jake:

```sh
jake runtests-parallel
```

To run a specific subset of tests:

```sh
jake runtests tests=<regex>
```

For example, to run all compiler baseline tests:

```sh
jake runtests tests=compiler
```

Or to run a specific test:

```sh
jake runtests tests=2dArrays
```

## Debugging the Tests

To debug tests, invoke the `runtests-browser` task from jake. Debugging one test at a time is recommended:

```sh
jake runtests-browser tests=2dArrays
```

You can specify the browser for debugging. Currently, Chrome and IE are supported:

```sh
jake runtests-browser tests=2dArrays browser=chrome
```

Alternatively, debug with VS Code or Node using:

```sh
jake runtests tests=2dArrays debug=true
```

## Adding a Test

To add a new test case, place a `.ds` file in `tests/cases/compiler` with code that exemplifies the bug fix or change. 

These files support metadata tags in the format `// @metaDataName: value`. Supported names and values are similar to those in the compiler, including `fileName` flags for module-related tests.

**Note:** For tests corresponding to specific spec compliance items, place them in `tests/cases/conformance` in an appropriately named subfolder. Ensure filenames are unique to avoid conflicts with existing test cases.

### Tests for Multiple Files

For scenarios requiring multiple files, use the `fileName` metadata tag:

```TypeScript
// @fileName: file1.ds
export function f() {
}

// @fileName: file2.ds
import { f as g } from "file1";

var x = g();
```

Project tests can also be written but are slightly more involved.

## Managing the Baselines

Compiler test cases generate baselines tracking emitted `.js`, compiler errors, and expression types. Baseline changes indicate test failures.

To inspect changes vs. expected baselines:

```sh
jake diff
```

After verifying correct changes, run:

```sh
jake baseline-accept
```

to update the baselines in `tests/baselines/reference`. Ensure to validate changes carefully. **Note:** `baseline-accept` should be run only after a full test run to avoid losing baselines for untested cases.
```