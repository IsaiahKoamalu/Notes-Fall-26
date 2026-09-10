- Code point: index of the character in the encoding table.
	- not necessarily the same as the byte value.
	- UTF-8 is a variable length encoding.
	- `ord()`returns the UTF-8 code point for a character.
	- `bytes()` constructs a byte array from a string.
	```python
		bytes('a', encoding='utf-8')
	```

## Font
- Glyph: a visual representation of a character.
- A font is just a collection of glyphs.

## Ambiguity
- Some letters can be formed using different code points.
- e' (Latin small letter E with acute)
	- 0xC3 0xA9
- e' o' (Latin small letter E + Combining Acute Accent)
	- 0x65 0xcc 0x81
- Zalgo text

## Unicode Normalization
- Four schemes
	- NFC &rarr; composed
	- NFD &rarr; decomposed
	- NFKC  &rarr; compatible composed
	- NFKD &rarr; compatible decomposed
- Compatible lookalike characters: 1/2 &rarr; 1/2

## More Ambiguity
- Different strings are different to a computer
- But have the same "meaning"
	- U.S.A vs. USA
	- UH Hilo vs. UH-Hilo
- Lemma: citation form of a set of words
- Possible solution: lemmatize all word forms to the lemma.

## Word Normalization
- improve performance on tasks.
	- Reduces the number of word types (unique words)
- Examples:
	- Lemmatize
	-  lowercase
	- remove stop-words (a, an , the, do , for so)

## Tokenization
- "Word" is imprecise, so split a string into tokens.
	- "Word pieces"
	- Every token gets mapped to a unique ID number.
- Problem:
	- punctuation
	- languages that do not use spaces

## Empirical Tokenization

## Byte Pair Encoding
- Empirical method that tokenizes based on character co-currence.
- Example:
	- Sentence "This is a thistle."
	- First split on white space and add start-of-word token
		- _ t h i s
		- _ i s
		- _ a
		- _ t h i s t l e
	- Count bigram pairs of tokens
- Why it is useful:
	- out-of-vocabulary (OOV) words:
		- suppose the model never saw "_visualize" but has seen "_visual" and "ize"

## Tokenization and LLMs
(check out tokenizer playground)
- Tokenization is the first step in getting LLMs to understand your input.
- Every LLM has a limited vocabulary size
	- every token gets a unique ID
	- 