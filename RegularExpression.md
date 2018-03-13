<br/>
<p align="center">
<img src="https://i.imgur.com/bYwl7Vf.png" alt="Learning Regular Expression">
</p><br/>

## What is Regular Expression?

A regular expression is a pattern that is matched against a subject string from
left to right. The word "Regular expression" is a mouthful, you will usually
find the term abbreviated as "regex" or "regexp". Regular expression is used for
replacing a text within a string, validating form, extract a substring from a
string based upon a pattern match, and so much more.

## 1. Literal Characters and Special Characters

The most basic regular expression consists of a single literal character, such as a.
It matches the first occurrence of that character in the string

##### 1.1 Literal Characters

The most basic regular expression consists of a single literal character.

<pre>
"cat" => The <a href="#T-T"><strong>cat</strong></a> runs so fast!
</pre>

##### 1.2 Special Characters

Because we want to do more than simply search for literal pieces of text, we need to reserve certain characters for special use.
There are 12 characters with special meanings.

![untitled](https://user-images.githubusercontent.com/36118701/37287284-09c11092-2637-11e8-84c4-c2e0e06db06a.png)

## 2. Characters Escape (Backslash)

Backslash `\` is used in regular expression to escape the next character. This
allows us to specify a symbol as a matching character including reserved
characters `{ } [ ] / \ + * . $ ^ | ?`. To use a special character as a matching
character prepend `\` before it.

For example, the regular expression `.` is used to match any character except
newline. Now to match `.` in an input string the regular expression
`(f|c|m)at\.?` means: lowercase letter `f`, `c` or `m`, followed by lowercase
character `a`, followed by lowercase letter `t`, followed by optional `.`
character.

<pre>
"(f|c|m)at\.?" => The <a href="#T-T"><strong>fat</strong></a> <a href="#T-T"><strong>cat</strong></a> sat on the <a href="#T-T"><strong>mat.</strong></a>
</pre>

##### 2.1 Meta Characters

![untitled](https://user-images.githubusercontent.com/36118701/37287532-94dd2382-2637-11e8-96f6-6e48db883e70.png)

##### 2.2 Characters Unicode

Unicode is a character set that aims to define all characters and glyphs from all human languages, living and dead. With more and more software being required to support multiple languages, or even just any language, Unicode has been strongly gaining popularity in recent years. Using different character sets for different languages is simply too cumbersome for programmers and users.

##### 2.2.1 Characters Unicode Set

<pre>
"\u0054" => <a href="#T-T"><strong>T</strong></a>he cat runs so fast!
</pre>

<a href="https://unicode-table.com/en/">See more unicode list here!</a>

##### 2.2.2 Characters Unicode Script

![untitled](https://user-images.githubusercontent.com/36118701/37287830-4c087e4e-2638-11e8-9493-aa9caba6852d.png)

##### 2.2.3 Characters Unicode General Category

![untitled](https://user-images.githubusercontent.com/36118701/37287914-8217181a-2638-11e8-8a06-ecb44e8915a4.png)

##### 2.3 POSIX Class

![untitled](https://user-images.githubusercontent.com/36118701/37288015-c1a57eae-2638-11e8-8e07-afe2787c37f0.png)

##### 2.4 Modifiers

![untitled](https://user-images.githubusercontent.com/36118701/37287447-6ba90026-2637-11e8-87d8-6af965afd27d.png)

##### 2.4.1 Case Insensitive

The `i` modifier is used to perform case-insensitive matching. For example, the
regular expression `/The/gi` means: uppercase letter `T`, followed by lowercase
character `h`, followed by character `e`. And at the end of regular expression
the `i` flag tells the regular expression engine to ignore the case. As you can
see we also provided `g` flag because we want to search for the pattern in the
whole input string.

<pre>
"The" => <a href="#T-T"><strong>The</strong></a> fat cat sat on the mat.
</pre>

<pre>
"/The/gi" => <a href="#T-T"><strong>The</strong></a> fat cat sat on <a href="#T-T"><strong>the</strong></a> mat.
</pre>

##### 2.4.2 Global search

The `g` modifier is used to perform a global match (find all matches rather than
stopping after the first match). For example, the regular expression`/.(at)/g`
means: any character except new line, followed by lowercase character `a`,
followed by lowercase character `t`. Because we provided `g` flag at the end of
the regular expression now it will find all matches in the input string, not just the first one (which is the default behavior).

<pre>
"/.(at)/" => The <a href="#T-T"><strong>fat</strong></a> cat sat on the mat.
</pre>

<pre>
"/.(at)/g" => The <a href="#T-T"><strong>fat</strong></a> <a href="#T-T"><strong>cat</strong></a> <a href="#T-T"><strong>sat</strong></a> on the <a href="#T-T"><strong>mat</strong></a>.
</pre>

##### 2.4.3 Multiline

The `m` modifier is used to perform a multi-line match. As we discussed earlier
anchors `(^, $)` are used to check if pattern is the beginning of the input or
end of the input string. But if we want that anchors works on each line we use
`m` flag. For example, the regular expression `/at(.)?$/gm` means: lowercase
character `a`, followed by lowercase character `t`, optionally anything except
new line. And because of `m` flag now regular expression engine matches pattern
at the end of each line in a string.

<pre>
"/.at(.)?$/" => The fat
                cat sat
                on the <a href="#T-T"><strong>mat.</strong></a>
</pre>

<pre>
"/.at(.)?$/gm" => The <a href="#T-T"><strong>fat</strong></a>
                  cat <a href="#T-T"><strong>sat</strong></a>
                  on the <a href="#T-T"><strong>mat.</strong></a>
</pre>

## 3. Negated Character (Caret)

Caret `^` symbol is used to check if matching character is the first character
of the input string. If we apply the following regular expression `^a` (if a is
the starting symbol) to input string `abc` it matches `a`. But if we apply
regular expression `^b` on above input string it does not match anything.
Because in input string `abc` "b" is not the starting symbol. Let's take a look
at another regular expression `^(T|t)he` which means: uppercase character `T` or
lowercase character `t` is the start symbol of the input string, followed by
lowercase character `h`, followed by lowercase character `e`.

<pre>
"(T|t)he" => <a href="#T-T"><strong>The</strong></a> car is parked in <a href="#T-T"><strong>the</strong></a> garage.
</pre>

<pre>
"^(T|t)he" => <a href="#T-T"><strong>The</strong></a> car is parked in the garage.
</pre>

##### 3.1 Negated Character Set

In general, the caret symbol represents the start of the string, but when it is
typed after the opening square bracket it negates the character set. For
example, the regular expression `[^c]ar` means: any character except `c`,
followed by the character `a`, followed by the letter `r`.

<pre>
"[^c]ar" => The car <a href="#T-T"><strong>par</strong></a>ked in the <a href="#T-T"><strong>gar</strong></a>age.
</pre>

## 4. Dollar (Dollar Sign)

Dollar `$` symbol is used to check if matching character is the last character
of the input string. For example, regular expression `(at\.)$` means: a
lowercase character `a`, followed by lowercase character `t`, followed by a `.`
character and the matcher must be end of the string.

<pre>
"(at\.)" => The fat c<a href="#T-T"><strong>at.</strong></a> s<a href="#T-T"><strong>at.</strong></a> on the m<a href="#T-T"><strong>at.</strong></a>
</pre>

<pre>
"(at\.)$" => The fat cat. sat. on the m<a href="#T-T"><strong>at.</strong></a>
</pre>

## 5. Full Stop (Dot)

Full stop `.` is the simplest example of meta character. The meta character `.`
matches any single character. It will not match return or newline characters.
For example, the regular expression `.ar` means: any character, followed by the
letter `a`, followed by the letter `r`.

<pre>
".ar" => The <a href="#T-T"><strong>car</strong></a> <a href="#T-T"><strong>par</strong></a>ked in the <a href="#T-T"><strong>gar</strong></a>age.
</pre>

## 6. Alternation (Pipe)

In regular expression Vertical bar `|` is used to define alternation.
Alternation is like a condition between multiple expressions. Now, you may be
thinking that character set and alternation works the same way. But the big
difference between character set and alternation is that character set works on
character level but alternation works on expression level. For example, the
regular expression `(T|t)he|car` means: uppercase character `T` or lowercase
`t`, followed by lowercase character `h`, followed by lowercase character `e` or
lowercase character `c`, followed by lowercase character `a`, followed by
lowercase character `r`.

<pre>
"(T|t)he|car" => <a href="#T-T"><strong>The</strong></a> <a href="#T-T"><strong>car</strong></a> is parked in <a href="#T-T"><strong>the</strong></a> garage.
</pre>

## 7. The Question Mark (Question Mark)

In regular expression the meta character `?` makes the preceding character
optional. This symbol matches zero or one instance of the preceding character.
For example, the regular expression `[T]?he` means: Optional the uppercase
letter `T`, followed by the lowercase character `h`, followed by the lowercase
character `e`.

<pre>
"[T]he" => <a href="#T-T"><strong>The</strong></a> car is parked in the garage.
</pre>

<pre>
"[T]?he" => <a href="#T-T"><strong>The</strong></a> car is parked in t<a href="#T-T"><strong>he</strong></a> garage.
</pre>

##### 7.1 Lookaround

Lookbehind and lookahead (also called lookaround) are specific types of
***non-capturing groups*** (Used to match the pattern but not included in matching
list). Lookaheads are used when we have the condition that this pattern is
preceded or followed by another certain pattern. For example, we want to get all
numbers that are preceded by `$` character from the following input string
`$4.44 and $10.88`. We will use following regular expression `(?<=\$)[0-9\.]*`
which means: get all the numbers which contain `.` character and  are preceded
by `$` character. Following are the lookarounds that are used in regular
expressions:

|Symbol|Description|
|:----:|----|
|?=|Positive Lookahead|
|?!|Negative Lookahead|
|?<=|Positive Lookbehind|
|?<!|Negative Lookbehind|

##### 7.1.1 Positive Lookahead

The positive lookahead asserts that the first part of the expression must be
followed by the lookahead expression. The returned match only contains the text
that is matched by the first part of the expression. To define a positive
lookahead, parentheses are used. Within those parentheses, a question mark with
equal sign is used like this: `(?=...)`. Lookahead expression is written after
the equal sign inside parentheses. For example, the regular expression
`(T|t)he(?=\sfat)` means: optionally match lowercase letter `t` or uppercase
letter `T`, followed by letter `h`, followed by letter `e`. In parentheses we
define positive lookahead which tells regular expression engine to match `The`
or `the` which are followed by the word `fat`.

<pre>
"(T|t)he(?=\sfat)" => <a href="#T-T"><strong>The</strong></a> fat cat sat on the mat.
</pre>

##### 7.1.2 Negative Lookahead

Negative lookahead is used when we need to get all matches from input string
that are not followed by a pattern. Negative lookahead is defined same as we define
positive lookahead but the only difference is instead of equal `=` character we
use negation `!` character i.e. `(?!...)`. Let's take a look at the following
regular expression `(T|t)he(?!\sfat)` which means: get all `The` or `the` words
from input string that are not followed by the word `fat` precedes by a space
character.

<pre>
"(T|t)he(?!\sfat)" => The fat cat sat on <a href="#T-T"><strong>the</strong></a> mat.
</pre>

##### 7.1.3 Positive Lookbehind

Positive lookbehind is used to get all the matches that are preceded by a
specific pattern. Positive lookbehind is denoted by `(?<=...)`. For example, the
regular expression `(?<=(T|t)he\s)(fat|mat)` means: get all `fat` or `mat` words
from input string that are after the word `The` or `the`.

<pre>
"(?<=(T|t)he\s)(fat|mat)" => The <a href="#T-T"><strong>fat</strong></a> cat sat on the <a href="#T-T"><strong>mat</strong></a>.
</pre>

##### 7.1.4 Negative Lookbehind

Negative lookbehind is used to get all the matches that are not preceded by a
specific pattern. Negative lookbehind is denoted by `(?<!...)`. For example, the
regular expression `(?<!(T|t)he\s)(cat)` means: get all `cat` words from input
string that are not after the word `The` or `the`.

<pre>
"(?&lt;!(T|t)he\s)(cat)" => The cat sat on <a href="#T-T"><strong>cat</strong></a>.
</pre>

##### 7.2 Greedy vs Lazy Matching

By default regex will do greedy matching , means it will match as long as
possible. we can use `?` to match in lazy way means as short as possible

<pre>
"/(.*at)/" => <a href="#T-T"><strong>The fat cat sat on the mat</strong></a>. </pre>

<pre>
"/(.*?at)/" => <a href="#T-T"><strong>The fat</strong></a> cat sat on the mat. </pre>

## 8. Character Group (Parenthesis)

Character group is a group of sub-patterns that is written inside Parentheses `(...)`.
As we discussed before that in regular expression if we put a quantifier after a
character then it will repeat the preceding character. But if we put quantifier
after a character group then it repeats the whole character group. For example,
the regular expression `(ab)*` matches zero or more repetitions of the character
"ab". We can also use the alternation `|` meta character inside character group.
For example, the regular expression `(c|g|p)ar` means: lowercase character `c`,
`g` or `p`, followed by character `a`, followed by character `r`.

<pre>
"(c|g|p)ar" => The <a href="#T-T"><strong>car</strong></a> is <a href="#T-T"><strong>par</strong></a>ked in the <a href="#T-T"><strong>gar</strong></a>age.
</pre>

## 9. Character Set (Square Bracket)

Character sets are also called character class. Square brackets are used to
specify character sets. Use a hyphen inside a character set to specify the
characters' range. The order of the character range inside square brackets
doesn't matter. For example, the regular expression `[Tt]he` means: an uppercase
`T` or lowercase `t`, followed by the letter `h`, followed by the letter `e`.

<pre>
"[Tt]he" => <a href="#T-T"><strong>The</strong></a> car parked in <a href="#T-T"><strong>the</strong></a> garage.
</pre>

A period inside a character set, however, means a literal period. The regular
expression `ar[.]` means: a lowercase character `a`, followed by letter `r`,
followed by a period `.` character.

<pre>
"ar[.]" => A garage is a good place to park a c<a href="#T-T"><strong>ar.</strong></a>
</pre>

## 10 Repetition

Following meta characters `+`, `*` or `{}` are used to specify how many times a
subpattern can occur. These meta characters act differently in different
situations.

##### 10.1 The Star

The symbol `*` matches zero or more repetitions of the preceding matcher. The
regular expression `a*` means: zero or more repetitions of preceding lowercase
character `a`. But if it appears after a character set or class then it finds
the repetitions of the whole character set. For example, the regular expression
`[a-z]*` means: any number of lowercase letters in a row.

<pre>
"[a-z]*" => T<a href="#T-T"><strong>he</strong></a> <a href="#T-T"><strong>car</strong></a> <a href="#T-T"><strong>parked</strong></a> <a href="#T-T"><strong>in</strong></a> <a href="#T-T"><strong>the</strong></a> <a href="#T-T"><strong>garage</strong></a> #21.
</pre>

The `*` symbol can be used with the meta character `.` to match any string of
characters `.*`. The `*` symbol can be used with the whitespace character `\s`
to match a string of whitespace characters. For example, the expression
`\s*cat\s*` means: zero or more spaces, followed by lowercase character `c`,
followed by lowercase character `a`, followed by lowercase character `t`,
followed by zero or more spaces.

<pre>
"\s*cat\s*" => The fat<a href="#T-T"><strong> cat </strong></a>sat on the con<a href="#T-T"><strong>cat</strong></a>enation.
</pre>

##### 10.2 The Plus

The symbol `+` matches one or more repetitions of the preceding character. For
example, the regular expression `c.+t` means: lowercase letter `c`, followed by
at least one character, followed by the lowercase character `t`. It needs to be
clarified that `t` is the last `t` in the sentence.

<pre>
"c.+t" => The fat <a href="#T-T"><strong>cat sat on the mat</strong></a>.
</pre>

##### 10.3 The Brace

In regular expression braces that are also called quantifiers are used to
specify the number of times that a character or a group of characters can be
repeated. For example, the regular expression `[0-9]{2,3}` means: Match at least
2 digits but not more than 3 ( characters in the range of 0 to 9).

<pre>
"[0-9]{2,3}" => The number was 9.<a href="#T-T"><strong>999</strong></a>7 but we rounded it off to <a href="#T-T"><strong>10</strong></a>.0.
</pre>

We can leave out the second number. For example, the regular expression
`[0-9]{2,}` means: Match 2 or more digits. If we also remove the comma the
regular expression `[0-9]{3}` means: Match exactly 3 digits.

<pre>
"[0-9]{2,}" => The number was 9.<a href="#T-T"><strong>9997</strong></a> but we rounded it off to <a href="#T-T"><strong>10</strong></a>.0.
</pre>

<pre>
"[0-9]{3}" => The number was 9.<a href="#T-T"><strong>999</strong></a>7 but we rounded it off to 10.0.
</pre>
