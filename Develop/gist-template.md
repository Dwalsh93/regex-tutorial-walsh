# Regex Tutorial: Matching a URL 

Throughout this tutorial you will learn about 11 different types of regular expressions and how to identify them, specifically within a given URL. A regular expression, or Regex, is a sequence of characters that specifies a search pattern. Usually these search patterns are used by string-searching operations on strings, or for input validation, like secure passwords and encryption. In this tutorial I'll show you what each regex concept covers and how using code snippets. 

## Summary

A regular expression is a sequence of characters that defines a search pattern. In this tutorial you'll learn a little bit about how Regular Expressions, or Regex, can be used to search for a webpages URL. 

URL – `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

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

There are 11 components of a regular expression that we will cover in today's tutorial, they are listed above in the table of contents. 

### Anchors

Anchors can be shown as `^ and $`, the purpose of an anchor is to match phrases that start with, or end with a certain character, using both together will find you the exact string you're searching for.

For example, in our expression above:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

you can see the `^` signifying the beginning of the URL and the `$` defining the end of the URL, meaning that our anchor here calls on everything within the URL. 

### Quantifiers

Quantifiers specify how many instances of a character, group or character class must be present in the input for match to be found. They indicate numbers of characters or expressions to match the preceding element one or more times. Quantifiers look like `* + ? and {}`, and are used in repeating patterns, or, sequences. 

In our URL:
 `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

You can see examples of all three. There are two asterisks used at the end of the URL, `*)` and `*\` these will match the strings that are followed by `)` and `\` show that it will match zero of the preceeding tokens. Our URL also has three question mark quantifiers `?`, these match the preceeding element one or more times, but as few times as possible. Finally our URL uses one set of `{}` curly braces, within the curly braces, you can see `{2,6}` these will match two to six from the previous token. 

### OR Operator

An OR operator or `| and []`  is used to match a string that is followed by one string OR the other string. For example, `Chicken(tenders/wings)` will find `Chicken` followed by EITHER `tenders` or `wings`. Alternatively, you could use `[]` to signify the opposite, so `Chicken[tenderswings]` would find `Chicken`, but neither `tenders` or `wings`.

Our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Uses several `[]` square bracket OR operators. You can see it first in `[\da-z.-]` and `[\/\w \.-]`. In this instance the `[]` matches a string without capturing any of the quantifiers within. 

### Character Classes

A character class is formed by putting a character class name between an open-character-class-operator, represented by `\ and .` For example, `\w` will match a single character that is a a `word` or an `underscore`. While `.` will match any character. 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

You can see `\d` used in the beginning of the expression `\da-z\.-]` this indicates that within the url there is a single character that is a digit. We see `\w` at the end of the expression here, `\w \.-]` indicating a word character, or alphanumeric character plus underscore. And finally the `.` is used 4 seperate times in our URL to indicate that it will match any character in that location.  

### Flags

When using regex, you can use a flag to affect the search, there are 6 flags that you can use. `i` - makes the search case insensitive, so it wont matter if you have A or a, your search will find either. `g` creates a global search, but does not return after the first match, so each new search begins at the end of the previous search. `m` is a multi-line flag that when enabled, `^ and $` will match the start and end of a line. Other examples are `s`, `u`, and `y` which create a "dotall", enables Unicode support and Sticky mode respectfully. 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

There are no flags in our specific example.

### Grouping and Capturing

Using the grouping and capturing operator, or `()`, allows the user to extract information from strings or data using your preferred programming language. For example, using the parentheses in `a(bc)` creates a capturing group with the value `bc`. 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

Grouping and captioning is used to group multiple tokens togteher for extracting a substring. Our example has four capturing groups `(https?:\/\/)`, `([\da-z\.-]+)`, `([a-z\.]{2,6})`, `([\/\w \.-]*)`. This allows for a substring to be verified. 

### Bracket Expressions

A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions. An example of a bracket expression is `[^a-zA-Z]`. In this example a string that does NOT have a letter from a-z (lowercase) or A to Z (uppercase), in this example the `^` acts as a negation of the expression. 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

Bracket expressions are shown three times, first, `[\da-z\.-]`, second `[a-z\.]`, and third `[\/\w \.-]`, these bracket expressions match strings that contain only what is within the expression. For our URL the second bracket shows the text can be any lower-case letter a-z as well as a backslash or period. 

### Greedy and Lazy Match

The quantifiers `* + {}` are greedy operators, they expand the match as far as they can through the provided text `<.+>` will match any character on or more times inside `< and >` . Whereas we can use a `?` to make that expression lazy, like `<.+?>`. 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

Our greedy operators are seen in the asterisks at the end, as well as the one pair of curly braces shown earlier in quantifiers. Our URL does not have lazy matches. 

### Boundaries

In regular expressions, boundaries are shown as `\b` and represents an anchor-like carat, matching positions where one side is a word character and the other side is not. The `\b` is negated by `\B` 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

There are no boundaries in our URL. 

### Back-references

Back-references in regular expressions are shown as `\1` using `\1` matches the same text that was matched by the first capturing group. Similarly, using `\2` and `\3` will do the same. 

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

It doesn't appear as if there is a back-reference, but if there were, a `\1` would reference our first grouping which is `(https?:\/\/)`. 

### Look-ahead and Look-behind

Look-ahead and look-behind match characters, but then give up the match, returning only the result, match or no match. They do not consume characters in the string, but only assert whether a match is possible or not.

In our URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` 

Our URL does not have a lookaround.

## Author

Dillon Walsh is a full stack developer: https://github.com/Dwalsh93