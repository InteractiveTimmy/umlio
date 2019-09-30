# UMLio Contributing Guide

## Setup

Before you can begin making contributions to this project, a few minor setup proceedures will need to be completed to validate the changes being made. Below are categorized groups to help guide the setup process.

### Platform Dependencies

Initially, the primary tools will need to be installed to begin making changes. These platform tools are as follows:

- **[Node (LTS)](https://nodejs.org/en/download/)**
- **[NPM](https://nodejs.org/en/download/)**
- **[Git](https://git-scm.com/downloads)**

### Repository Setup

After the platform dependencies are installed, a forked repository can be initialized in order to create a safe place to generate changes against the current development branch. To do this, fork the [UMLio](https://github.com/InteractiveTimmy/umlio) repository via its github page into your own user account's repositories. From there, one can clone the forked repository via the following Git command line:

```text
git clone https://github.com/username/umlio
```

Once the cloning process is complete, change the terminal's active directory to `./umlio` using the following command line:

```text
cd umlio
```

### Project Dependencies

Now that the repository has been cloned successfully to the local harddrive, the project's dependencies can be installed using one command:

```text
npm install
```

This will install all dependencies required to develop, test, and build any changes that are to be made.

## Building

Building the project after a change has been made is as simple as running a single line command:

```text
npm run build
```

This will run the following commands in order to fully build the project into a consumable form:

- `npm run lint` - lints the source files
- `npm run test` - runs the testing suite
- `npm run docs` - builds the documentation files
- `npm run transpile` - transpiles the source files
- `npm run compile` - compiles the transpiled source files
- `npm run compress` - compresses the compiled files

Additionally, the following command can be used to actively build any changes being made. This will automate the `build` process, saving some time during development:

```text
npm run build -- --watch
```

## Running

While running the project wont result in any real results unless an input is provided, there are samples located in the `./samples` directory that will run against the files located in the `./build` directory. These serve as **functional tests** and can be ran using the following command:

```text
npm run samples:subdirectory
```

The subdirectory will identify any folders located within the `./samples` directory and will launch the file named `index.js` from within the targetted directory.

## Making Changes

All changes that occur within this project must undergo a process that identifies how they should be implimented, from design to completion. Below are the steps in which we recommend all changes proceed through.

### Proposal Step

All changes must be proposed. This could be via an [issue](https://github.com/InteractiveTimmy/umlio/issues) or via a [pull request](https://github.com/InteractiveTimmy/umlio/pulls). The proposal step must include some details indicating the following:

- What the change entails
- Why the change is needed

While these can be vaguely interpreted based on how the issue is presented, it is recommended to provide sufficient details in these categories. Once the proposal is approved, the design step can begin.

### Design Step

In order to validate that the coding efforts involved will address the changes proposed, a few design steps will be necessary. This can consist of as few details as what is changing functionality and where the changes will live, to as many details as multiple UML digrams can provide. The primary goal of this step is to provide a clear understanding of what the plan-of-approach is to achieving the proposed changes. A list of possible design documents would include:

- UML diagrams
- detailed text documents
- unimplemented files with short descriptions

### Implementation Step

In order to make the changes proposed, they need to be implemented of course. This can consist of efforts in source code, documentation details, testing suites and more. It is recommended to follow a specific flow and check-ins with contribution gate-keepers to make sure this step is going as planned, but for most changes, especially small ones, most of these steps can occur in any order:

- make changes in tests
- make changes in source files
- make changes in documentation
- review all changes
- run tests as thoroughly as possible

Once the changes have been fully made, be sure to perform a self-review of the work that has been completed to ensure that everything complies with the standards set in this article.

After implementation is complete, update or create a [pull request](https://github.com/InteractiveTimmy/umlio/pulls), providing as much detail as possible in regards to how it was implemented. There may be changes that don't meet the standards expressed in this article, so some additional changes may be necessary based on the feedback provided in the [pull request](https://github.com/InteractiveTimmy/umlio/pulls).

### Merge Step

Merging will be an administrator-only step in which all of the proposed changes will be squashed and merged directly into the development branch. Upon the next release, all changes that have made it into the development branch will be merged into the master branch and tagged for a release build.

## Documentation

Documenting all methods, classes, and miscellaneous files is important to keep code clear and understandable for future revisions and review. For any file changes that occur within source code directories, a strict pattern must be followed when applicable. Below are a collection of examples to help guide document generation:

### Entry File Documentation

```typescript
// Copyright

/**
 * Summary
 *
 * @remarks
 * Full Description
 *
 * @privateRemarks?
 *
 * @packageDocumentation
 */

import Plugin from './plugin/index';

export {
  Plugin,
}
```

### Functional File Documentation

```typescript
import otherMethod from './other-method';

/**
 * Summary
 * @deprecated?
 * @alpha | @beta | @internal | @public & @preapproved?
 * {@inheritDoc otherMethod}?
 *
 * @remarks
 * Full Description
 *
 * @privateRemarks?
 *
 * @example
 *
 * @typeParam? T - short description
 * @param? x - short description
 * @returns - short description
 *
 * @sealed
 */
 export default method<T>(x: T): T {
   return x;
 }
```

### Class File Documentation

```typescript
import OtherClass from './other-class';

/**
 * Summary
 *
 * @deprecated?
 * @alpha | @beta | @internal | @public & @preapproved?
 * {@inheritDoc OtherClass}?
 *
 * @remarks
 * Full Description
 *
 * @privateRemarks?
 *
 * @example
 *
 * @typeParam? T - short description
 * @param? value - short description
 *
 * @sealed
 */
export default class ExampleClass<T> extends OtherClass {
  // Do not declare values before constructor, end each line with `;`
  // All class members must be scoped
  // All class members must be alphabetical by group [properties, constructor, getters/setters, instance methods, static methods]

  /** short x description */
  private pX: number;

  /** short y description */
  protected y: string;

  /** short z description */
  public z: boolean;

  public constructor(x: number, y: string, z:boolean) {
    super();

    this.pX = x;
    this.y = y;
    this.z = z;
  }
  
  // getters and setters first
  /**
   * Summary
   * @deprecated?
   * @alpha | @beta | @internal | @public & @preapproved?
   * {@inheritDoc OtherClass.method}
   *
   * @returns - short description
   *
   * @readonly? @virtual? @override?
   */
  public get pX(): number {
    return this.pX;
  }

  /**
   * Summary
   *
   * @deprecated?
   * @alpha | @beta | @internal | @public & @preapproved?
   * {@inheritDoc OtherClass.method}
   *
   * @remarks?
   *
   * @privateRemarks?
   *
   * @typeParam? T - short description
   * @param? x - short description
   * @returns - short description
   *
   * @virtual? @override?
   */
  public doSomething<T>(x: T): T {
    this.pX = x;

    return this.pX;
  }
}
```

## Testing

Tests are necessary to prove that an implemented change works against a proposed design. Tests should be broken down into appropriate groups to help organize what the testing scope of each section entails. These methods will be scoped and grouped to help identify what is being targetted.

Groups:

- **object** - object to be tested
- **type** - testing type, should be `unit`, `integration`, and `functional`
- **member** - member of class being method, should be `property` or `method()`
- **clause** - statement being tested

Examples:

```javascript
object('objectName') {
  type('unit') {
    member('member1') {
      clause('clause 1') { /* test logic */ }
      clause('clause 2') { /* test logic */ }
    }
    member('member2()') {
      clause('clause 1') { /* test logic */ }
      clause('clause 2') { /* test logic */ }
    }
  }
  type('integration') {
    member('member1') {
      clause('clause 1') { /* test logic */ }
      clause('clause 2') { /* test logic */ }
    }
  }
}
```

All testing suites must be located within the projects `./tests` directory and must reflect the file path of the file it tests in the `./src` directory. Below is an example of this structure:

```text
./src/group/class/class.ts // source code file to be tested
./tests/group/class/class.ts // associated testing suite file
```

## Git Guidelines

To help maintain a consistent style for changes in this repository, a strict standard is enforced. Below are details that cover the enforced conventions that all changes must meet. Most of the provided standards are built around the conventions described in the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) project.

### General Conventions

#### Grammar

While grammar can be a diverse topic with many different standards, adhering to simple rules can help make it much easier to understand the purpose of the provided change. To promote short and simple grammar, all conventions should adhere to [simple present](https://www.grammarly.com/blog/simple-present/) tense, and lack a subject when the convention does not reference an issue. Additionally, all [determiners](http://google.com/search?q=determiner) should be avoided when possible.

Examples:

- **acceptable without issue** - `generate new method`
- **acceptable with issue** - `new method does not work`
- **not acceptable [with subject]** - `i generate a new method`
- **not acceptable [wrong tense]** - `generating new method`
- **not acceptable [unnecessary determiner]** - `generate the new method`

Types:

- **build** - changes that affect built files
- **ci** - changes that impact ci files
- **chore** - changes that impact tooling and scripts
- **docs** - changes that only impact documentation
- **feat** - changes that are adding functionality
- **fix** - changes that fix an issue
- **perf** - changes that improve functionality
- **refactor** - changes that are uncategorizable
- **revert** - changes that remove existing functionality
- **style** - changes that modify code style
- **test** - changes that are adding tests

### Branch Conventions

Branch naming conventions align closely with those exibited via the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) project. Definitions of each section parameter are as follows:

- **type** - must align with the [types](####-types) section of this guide.
- **issue-id** - when applicable, must reference an [issue](https://github.com/InteractiveTimmy/umlio/issues) ID.
- **short-description** - short description that follows [grammar](####-grammar) guidelines and match the referenced [issue](https://github.com/InteractiveTimmy/umlio/issues)

Format:

```text
<type>/<issue-id?>/<short-description>
```

Examples:

- **new feature** - `feat/add-new-methods`
- **new issue** - `fix/1234/methods-do-not-work`

### Commit Conventions

Commit formatting conventions align closely with those exibted via the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) project. Definitions of each section parameter are as follows:

- **type** - must align with the [types](####-types) section of this guide
- **subject** - short description that follows [grammar](####-grammar) guidelines
- **body** - long description that follows [grammar](####-grammar) guidelines
- **footer** - optional long description that follows [grammar](####-grammar guidelines when a breaking change may be introduced by the changes

Format:

```text
<type>: <subject>
<blank-line>
<body>
<blank-line?>
<footer?>
```
