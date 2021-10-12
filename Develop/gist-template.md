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

In our email sample we use caret `^` at the start of the expression `/^([a-z0-9_\.-]+)...` in order to match what comes immediately after it. We use grouping by placing multiple tokens inside a parenthesis and square brackets so our caret will apply to this group.

the caret will take advantage of Character Classes/Sets and match any alphanumeric combination (lower case), including the underscore `_`, dash `-` or dot/period `. ` characters.

valid examples:  jerry, jerry1, jerry_1, jerry-1, jerry.1\
invalid examples: jerry%, jerry&

We are also using the dollar sign `$` at the end of the expression in order to match the tokens grouped inside the preceding parenthesis and square brackets. `([a-z\.]{2,6})$`

in this case we will only accept letters characters (lowercase), the dot/period `. ` character and must match between 2 and 6 of the preceding tokens (see quantifiers below)

valid examples: .com, io, .co.uk

### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found https://docs.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions. The following quantifiers are examples of what is available for use in regular expressions
* `*`       - Match zero or more times
* `+`       - Match 1 or more times
* `? `       - Match zero or one time.
* ` {n}`   - Match exactly n times.
* ` {n, m} ` - Match from n to m times.


in our example we use the plus sign `+` and {2,6} as quantifiers. the plus sign `+` appears right after the closing of the square brackets in `([a-z0-9_\.-]+)` and `([\da-z\.-]+)` which indicates that we need at least one of the tokens in the square brackets to match in order to validate the expression. by using the plus sign quantifier in this case, we make sure not to allow for a null group (Match 1 or more times). The {2,6} quantifier means that we must match between 2 and 6 of the preceding tokens

valid examples for `([a-z0-9_\.-]+)`: 12a, tttt2_\
invalid examples for `([a-z0-9_\.-]+)`: 12&, rrr% or no tokens present

valid examples for `([\da-z\.-]+)`: 12a, tttt2_\
invalid examples for `([\da-z\.-]+)`: 12&, rrr% or no tokens present

valid examples for `([a-z\.]{2,6})`: .com , .io\
invalid examples for `([a-z\.]{2,6})`: c, 1122222222 no tokens present

### OR Operator

The Or operator is not specifically used in this regular expression. However, it can be achieved in regular expressions by the use of the `|` character. This will match the characters to the left or right of `|`.

It is important to notice that in our example, tokens inside the square brackets will act as an Or
* [a-z0-9_\.-] will match any lowercase letter `Or` Digit `Or` dot `Or` dash

### Character Classes

Character Classes or Character Sets allows us to match any symbol from a character set. They are usually represented by square brackets but can also be represented with a `\` in front of a predefined letter; an example of this can be seen in our regular expression

* This section `[a-z0-9_\.-]` will match any digits between 0 and 9 by using a range `0-9`

* This section `[\da-z\.-]` achieves the same matching for numbers/digits by using `\d'

Please see bracket expressions below for a more in-depth analysis

### Flags

Flags are not used in this regular expression. However, the forward slash components `/` indicates the start and end of a regular expression. After the closing forward slash, expression flags can be added. some examples can be `g` for global search or `m` for multiline

### Grouping and Capturing

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together and apply a quantifier as described in the Quantifiers section. these groups can be referenced in a replacement or a substring extracted from them.

### Bracket Expressions
A bracket expression is a list of characters enclosed by ‘[’ and ‘]’. We can use bracket expressions to match single characters or a range of characters in a list. In our example we can see the use of bracket expressions by looking at the characters inside the square brackets `[...]`

* `[a-z0-9_\.-]` it will match any alphanumeric combination and it can include the underscore `_`, dash `-` or dot/period `.` characters.\
-
  - valid examples: just1ne, justine_2, just.ine
  - invalid examples: just&, just%
* `[\da-z\.-]` it will match any digit and letter combination and it can include the dash `-` or dot/period `.`
-
  - valid examples: google, net1, just.ine\
  - invalid examples: just&, just_
* `[a-z\.]` it will match any letter combination and it can include a dot/period `.`\
-
  - valid examples: .com, .co
  - invalid examples: com&, net_


### Greedy and Lazy Match

This section applies to quantifiers like `*,+,?,{n},{n,m}` Quantifiers can be greedy (default) or lazy (by appending a `?` behind). When doing a Greedy match, they cause the regular expression engine to match as many occurrences of particular patterns as possible.

When doing a Lazy Match, it causes the regular expression engine to match as few occurrences as possible

in our example we use the plus sign `+` and {2,6} in their greedy forms to ensure that we don’t have empty sets

### Boundaries

We are not using boundaries for our expression, however when creating a regex, we can use the metacharacter `\b` to find whole words. This is beyond the scope of this tutorial

### Back-references

We are not using back-references for our expression, however they can be used in conjunction with parentheses to create a capturing group and match the same text as previously matched. This is beyond the scope of this tutorial

### Look-ahead and Look-behind

We are not using Look-ahead and Look-behind in our expression and are beyond the scope of this tutorial

## Author

My name is Guillermo Fernandez, I’m currently switching careers from the Health Care industry to the
Technology Field. Having a blast while doing it!
[Checkout my GitHub profile](https://github.com/gfernandez25)
