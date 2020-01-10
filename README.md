# Git Guideline

> Commit Message Guidelines

We have rules over how our git commit messages can be formatted. This leads to **more**
**readable messages **that are easy to follow when looking through the** project history**.  But also,
it makes it easier to **write automated tools** on top of it like **generating the change log**.
# #Commit Message Format

Each commit message consists of a **header**, a **body** and a **footer**.  The header has a special
format that includes a **type**, a **scope** and a **subject**:

```none
<type>[optional scope]: <subject>

[optional body]

[optional footer(s)]

```

The **header** is mandatory and the **scope** of the header is optional.
The **body **and the** footer(s)** are optional.
Any line of the commit message cannot be longer than **80 characters**! This allows the message to be easier to read.
# #Specification


## 1-Type

Must be one of the following:
* **feat**: Add a new feature (equivalent to a _MINOR_ in [Semantic Versioning](https://semver.org/))
* **fix**: Fix a bug (equivalent to a _PATCH_ in [Semantic Versioning](https://semver.org/))
* **perf**: A code change that improves performance
* **docs**: Documentation only changes
* **style**:  Code style change (white-space, formatting, semi-colons, indentation, etc)
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **test**: Adding missing tests or correcting existing tests
* **revert**: The commit reverts a previous commit
* **chore**: Update something without impacting the user (ex: bump a dependency in package.json)
* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, npm)
* **ci**: Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)


```
docs: correct spelling of CHANGELOG

```


## 2-Scope

A scope may be provided to a commit’s type, to provide additional contextual information and is contained within parenthesis.

```
feat(parser): add ability to parse arrays

```


## 3-Subject

The subject contains a succinct description of the change:
* limit to **50 characters**
* use the **imperative, present tense**: "change" not "changed" nor "changes"
* don't capitalize the first letter
* no dot (.) at the end


```
docs(changelog): update changelog to beta.5

```


## 4-Body

Just as in the **subject**, use the imperative, present tense: "change" not "changed" nor "changes".
The body should include the motivation for the change and contrast this with previous behavior.
> _Explain what and why vs. how_

```
fix(release): need to depend on latest rxjs and zone.js

The version in our package.json gets copied to the one we publish, and users need the latest of these.

```


## 5-Footer

A footer’s value _MAY_ contain spaces and newlines, and parsing _MUST_ terminate when the next valid footer token/separator pair is observed.
The footer should contain any information about **Breaking Changes** and is also the place to add a [closing reference to an issue](https://help.github.com/articles/closing-issues-via-commit-messages/) if any. For closing issues you _MUST use the keyword _`fix`

```
fix: correct minor typos in code

see the issue for details on typos fixed.

Reviewed-by: Nazer
fix #133

```


## @- Revert

> If the commit reverts a previous commit, it should begin with `revert:`, followed by the header of the reverted commit. In the body it should say: `This reverts commit <hash>.`, where the hash is the SHA of the commit being reverted.

```
revert: refactor!: drop support for Node 6

This reverts commit 676104e

```


## @- Breaking Changes

> Breaking changes MUST be indicated in the type/scope prefix of a commit, and/or as an entry in the footer.

```
refactor!: drop support for Node 6

BREAKING CHANGE: refactor to use JavaScript features not available in Node 6.

```

> If included as a **footer**, a breaking change MUST consist of the uppercase text `BREAKING CHANGE`, followed by a colon, space, and description

```
refactor: drop support for Node 6

BREAKING CHANGE: refactor to use JavaScript features not available in Node 6.

```

> If included in the **type/scope prefix**, breaking changes MUST be indicated by a `!` immediately before the `:`. If `!` is used, `BREAKING CHANGE:` CAN be omitted from the footer section, and in that case the commit **Body** SHALL be used to describe the breaking change.

```
refactor!: drop support for Node 6

Refactor to use JavaScript features not available in Node 6.

```
