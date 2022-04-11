# URL Validation with Regex

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

## Summary

The Regular Expression, or Regex, above can be used to validate whether or not a string of characters is a valid URL.

Regex is used to define a search query that is more complex that a simple find that you would find in any text editor. Some text editors do support Regex making them well suited to complex text manipulation such as matching, locating, and managing that text. They can be used on any strings of text such as text in a documents, or even files in the filesystem.

The purpose of this document, or Gist, is to save this code snippet and explanation for further use and/or to share it with others.

A Regex must be wrapped in the / character, otherwise it would be treated as any other string of text. It is made up of the compenents discussed below.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The Anchors `^` and `$` are placed at the begining and end of a Regex. In addition to the wrapping of the whole expression in the `/` character, these characters are how a search function knows when the expression starts and ends.

### Quantifiers

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The first Quantifier in the expression is the `?` character. A Quantifier counts how many times a character or group must be present for a match to be found. The character or group used is the one immediately preceding the `?`. So in this case, it is the `s` character.

The `?` appears again, this time with the group `(https?:\/\/)?`.

In both cases, the character or group must be matched zero to one times. The s character can be present zero or one time making both https (one time) and http (zero times) valid. However, only the s character may appear zero or one times. The http portion must appear and may not be followed by a character other than s. http and https are valid. httg or httpg are not valid.

The next quantifier in the Regex is the `+` character. This means that the preceding character or group must appear at least onece, but may appear as many times as possible. In this case `[\da-z\.]`

The next qualifier is `{}`. Here it is `{2,6}`. It is preceeded by `[a-z\.]` meaning that group must appear between 2 and 6 times.

The final quantifier is the `*` character. The `*` quantifier can match zero or more times unlike the `?` which matches zero or one times, or `+` which matches one or more times. It is preceeded by `[/\w.\.-]` so that group may appear zero to infinity times.

### Grouping Constructs

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Groups are contained in parenthesis `()` and are used to create individual groups that are processed as a whole and the result then passed to the Regex as a whole.

Each of the following will be matched before being applied in another order based on additional brackets:

- `(https?:\/\/)?` - only the http or https portion of the Regex is matched
- `([\da-z\.-]+)` - `[\da-z\.-]` will be matched one or more times
- `([a-z\.]{2,6})` - the `[a-z\.]` will be matched 2 to 6 times
- `([\/\w \.-]*)` - `[\/\w\.-]` will be matched 1 or more times

### Bracket Expressions

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Charcters within `[]` are characters to be matched or included.

- `[\da-z\.-]` - `\d` means any number, a-z means any lowercase letter, `\.` requires a `.` be matched, and `-` means a `-` needs to be matched
- `[a-z\.]` - `a-z` is any lowercase letter and `\.` requires a `.`
- `[\/\w \.-]` - `\/` measn that a `/` is required, `\w` means a letter or number character, `""` is a space, `\.` a `.`, and `-` is a `-`.

Each set in brackets needs to be resolved before any Anchors are used.

### Character Classes

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

- `\d` is any number `0-9`
- `\w` any alphanumeric character such as `a-z`, `A-Z`. `_.` and `0-9`
- `a-z` is any lowercase letter

### The OR Operator

`|` is an Or Operator and allows for an either or between two groups, brakets, classes, or characters. This Regex doesn't use an Or Operator.

### Flags

Flags modify how the other parts of a Regex work.

- `i` - ignores casese
- `g` - global - for all occurrences
- `s` - makes . match newlines
- `m` - makes a Regex be able to seperate into multiple lines, each with a beginning `^` and end `$`
- `y` - is used in the case of a document with a `lastIndex` property
- `u` - deals with what characters are possible

There are no Flags in this Regex.

### Character Escapes

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

A `\` is used to allow a special character that might otherwise be used as an operator. It turns the character into a literal. In this Regex:

- `\/` allows a `/`
- `\.` allows a `.`

## Author

**William Reising** - Student at the UCI Coding Bootcamp.
[Twitter](https://twitter.com/reisingtech)
[GitHub](https://github.com/wreising)
[email](mailto:william@reising.dev)