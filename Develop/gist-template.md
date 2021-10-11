# Regular Expression Tutorial: matching an email

The purpose of this tutorial is to explore regular expressions. We will accomplish this by breaking down an example of a pattern that will check that the input provided matches an email address. Regular Expressions can be defined in its simplest form as a pattern of text that can be used to match any combination of characters in a string. They can be used to validate input, perform searches and even process text.

## Summary
This tutorial will provide a walkthrough of a regular expression used to match an email pattern.
The regular expression will look like the code below and we will walk through each component that makes it work.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors in regular expressions are represented by the caret `^` and dollar sign `$`. They are not used to match any character; they match a position before or after characters.

* ^ – Use caret at the beginning of the text.
* $ – Use the dollar sign for the end of the text.

In our email sample we use caret `^` at the start of the expression `/^([a-z0-9_\.-]+)...` in order to match what comes immediately after it. We also using grouping by placing multiple tokens inside a parenthesis so our caret will apply to this group.

it will match any alphanumeric combination and it can include the underscore `_`, dash `-` or dot `.` characters.

valid examples:  jerry, jerry1, jerry_1, jerry-1, jerry.1\
invalid examples: jerry%, jerry&

We are also using the dollar sign `$` at the end of the expression in order to match the tokens grouped inside the preceding parenthesis. `([a-z\.]{2,6})$`

in this case we will only accept alpha characters (letters) and the dot `. ` character and must match between 2 and 6 of the preceding tokens (see quantifiers below)

valid examples: .com, io, .co.uk

### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found https://docs.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions. The following quantifiers are examples of what is available for use in regular expressions
* `*`       - Match zero or more times
* `+`       - Match 1 or more times
* `?`       - Match zero or one time.
* `{ n }`   - Match exactly n times.
* `{n , m}` - Match from n to m times.


in our example we use the plus sign `+` and {2,6} as quantifiers. the plus sign `+` appears right after the closing of the square brackets in `([a-z0-9_\.-]+)` and `([\da-z\.-]+)` which indicates that we need at least one of the tokens in the square brackets to match in order to validate the expression. by using the plus sign quantifier in this case, we make sure not to allow for a null group (Match 1 or more times). The {2,6} quantifier means that we must match between 2 and 6 of the preceding tokens

valid examples for `([a-z0-9_\.-]+)`: 12a, tttt2_\
invalid examples for `([a-z0-9_\.-]+)`: 12&, rrr% or no tokens present

valid examples for `([\da-z\.-]+)`: 12a, tttt2_\
invalid examples for `([\da-z\.-]+)`: 12&, rrr% or no tokens present

valid examples for `([a-z\.]{2,6})`: .com , .io\
invalid examples for `([a-z\.]{2,6})`: c, 1122222222 no tokens present

### OR Operator

### Character Classes

### Flags

the forward slash component `/` indicate the start and end of a regular expression. After the closing forward slash, expression flags can be added

### Grouping and Capturing

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together.

### Bracket Expressions

- must be at the end so is not treated as a range generator

### Greedy and Lazy Match
The quantities n and m are integer constants. Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible. Appending the ? character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible


### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
![image](https://user-images.githubusercontent.com/82284313/136739758-879440ef-53e9-4015-abe9-3d54c1d2b34a.png)
