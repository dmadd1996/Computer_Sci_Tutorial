# Email Regex Tutorial

This tutorial readMe will go over the components of email validation regex.

## Summary

Email validation covers some of the regex components expanded upon below. Each part of the following example will be explained in their own separate sections, as well as some other components not shown in the following example.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

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

These are special sequences which match an empty substring.

"^" matches at the beginning of the target string
"$" matches at the end of the target string
"\b" matches on a word boundary, i.e., the previous or subsequent character is not a word character

In the given email regex, you can see anchors at the beginning and end, as the email should be a single string.

### Quantifiers

Regular expressions use quantifiers to generate unbounded matching possibilities and other matching amount specifications. An atom can optionally be followed by one of these quantifiers:
 *   representing 0 or more occurrences of the atom,
 +   representing 1 or more occurrence of the atom,
 ?   representing 0 or 1 occurrences of the atom,
the bound {n}   representing exactly n occurrences of the atom,
the bound {m,n}   representing between m and n occurrences of the atom.
The quantifier can optionally be followed by "?" indicating that the match be minimal (non-greedy, reluctant) as opposed to the default maximal (greedy) match.

In the email regex example, you can see that the "username" section of the email and the domain before the ".com" can be matched any number of times more than 1. For the end of the email (.com, .gov, etc.) it can only be matched between 2 and 6 times with a greedy match (default).

### OR Operator

There are no Alternation operators in this email regex, but they are denoted by the "|" symbol and function much like how they do in javascript and other languages. The 

### Character Classes

Defines the characters that can be within the accepted criteria. Dots are used to pick up any character except for line breaks.

In this example, we see four instances of ranges (a-z and 0-9) and the digit class (\d) and three dots (.). In this case, the backslash before each dot character is defining the dot can be matched in the string ("derek.madderom" is an okay match).

### Flags

Flags are codes that can be added to a pattern to modify the acceptable criteria for the pattern.

i -With this flag the search is case-insensitive: no difference between A and a (see the example below).
g -With this flag the search looks for all matches, without it – only the first match is returned.
m -Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
s -Enables “dotall” mode, that allows a dot . to match newline character \n.
u -Enables full Unicode support. The flag enables correct processing of surrogate pairs. More about that in the chapter Unicode: flag "u" and class \p{...}.
y -“Sticky” mode: searching at the exact position in the text (covered in the chapter Sticky flag "y", searching at position)

### Grouping and Capturing

The elements are being grouped with parenthases so that multiple characters are treated as a single unit. They are not necessary for our email validator to work but are useful for extracting a substring or using a backreference.

### Bracket Expressions

These define the beginning and end of a character set "[...]".

### Greedy and Lazy Match

The greedy and minimal (non-greedy) quantifiers differ only in terms of extraction of the matched portion. For example, consider the string AABBBB matched against these two patterns:
^(\w+)(B+)$          (greedy)
^(\w+?)(B+)$         (minimal)
In the former case, \w+ would match AABBB leaving a single B to match B+. In the latter case \w+ would minimally match only AA, leaving BBBB to match B+.

### Boundaries

Defines what the character being matched is surrounded by. For example testing \bis\b on the string This island is beautiful, will only return the third word "is" because /b denotes that the target is a word surrounded by non-letter characters.

### Back-references

Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag. Here’s how:

For example, say that our email regex requires that for some reason, the username (*example*@example.com) must match the domain (example@*example*.com), we could do this:

/^([a-z0-9_\.-]+)@(\1)\.([a-z\.]{2,6})$/

Notice the "\1" referencing the first group in parentheses

### Look-ahead and Look-behind

Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions just like the start and end of line, and start and end of word anchors. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match.

There is no look-ahead or behind in this example

## Author

My name is Derek Madderom, full-stack web dev.

github.com/dmadd1996
