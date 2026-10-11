## Regular Expressions
- Way to describe a set of strings based on common characteristics shared by each string in the set.
- Used to search, edit, or manipulate text and data.
- Requires a specific syntax
	- varies between programming languages
- Regex vary in complexity
- understanding basics allows you to create any regex.

## In Java and Other Languages
- Many different flavors: grep, Perl, Tc, Python, PHP, awk.
- Javas `java.util.regex` API is most similar to that found in Perl.

## How Regex is represented in Java
- Three primary packages in `java.util.regex`
- **Pattern:** a `Pattern` object is a compiled representation of the regex.
	- `Pattern` class provides no public constructors.
	- creating a pattern requires invoking one of its `public static compile` methods (this returns a `Pattern` object)
	- these methods accept a regex as the first argument.
- **Matcher:** A `Matcher` object is the engine which interprets the pattern and performs match operations against an input string.
	- `Matcher` also has no public constructors.
	- `Matcher` objects are obtained by invoking the `matcher` method on a `Pattern` object.
- **PatternSyntaxException:** A `PatternSyntaxException` object is an unchecked exception that indicates a syntax error in a regex pattern.

## String Literals
- String literal is most basic form of pattern matching.
	- EX:  if `regex = 'foo'` and `string = 'foo'` then match will succeed since the strings are identical.

## Match Indices
```
Enter your regex: foo  
Enter input string to search: foo  
I found the text "foo" starting at index 0 and  
ending at index 3.
```
- Each char in the string resides in its own cell, with the index positions pointing between each cell.
- So... string `foo` starts at index $0$ and ends at index $3$ even though the chars themselves only occupy cells $0,1,2$ .

## Subsequent Matches
- Notice some overlap
	- the start index of the next match is the same as the end index of the previous match.

```
Enter your regex: foo  
Enter input string to search: foofoofoo  
I found the text "foo" starting at index 0 and ending at index 3.  
I found the text "foo" starting at index 3 and ending at index 6.  
I found the text "foo" starting at index 6 and ending at index 9.
```

## Metacharacters
- The API also supports special characters that affect the way a pattern is matched.
```
Enter your regex: cat.  
Enter input string to search: cats  
I found the text "cats" starting at index 0 and ending at index 4.
```
- The match still succeeds because the dot "." is a metacharacter that means "any character".

## Supported  Metacharacters
- Supported metacharacters: `<([{\^-=$!|]})?*+.>`

## Escaping Metacharacters
- Two ways
	- precede the character with a backslash
	- enclose it within `\Q` and `\E`

## Character Classes
