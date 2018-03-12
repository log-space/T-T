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

## 2. Characters Set (Backslash)

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

## 4. Full Stop (Dot)

Full stop `.` is the simplest example of meta character. The meta character `.`
matches any single character. It will not match return or newline characters.
For example, the regular expression `.ar` means: any character, followed by the
letter `a`, followed by the letter `r`.

<pre>
".ar" => The <a href="#T-T"><strong>car</strong></a> <a href="#T-T"><strong>par</strong></a>ked in the <a href="#T-T"><strong>gar</strong></a>age.
</pre>

## 5. Alternation (Pipe)

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
