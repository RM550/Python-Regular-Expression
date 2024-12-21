### 📄 Problem 2.1 Match litrel text

Create a regular expression to exactly match this gloriously contrived sentence:

The punctuation characters in the ASCII table are: !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~.


### 📝 Answer

```python
import re

# The given sentence
sentence = r'The punctuation characters in the ASCII table are: !"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~.'

# Regular expression to exactly match the sentence
regex = r'^The punctuation characters in the ASCII table are: [!"#$%&\'()*+,-./:;<=>?@[\\\]^_`{|}~.]+$'

# Check if the sentence matches the regular expression
match = re.match(regex, sentence)

if match:
    print("The sentence matches the regular expression.")
else:
    print("The sentence does not match the regular expression.")
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Sentence:

The sentence to match is:

The punctuation characters in the ASCII table are: !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~

This sentence includes a string of punctuation characters from the ASCII table.

#### 🛠️ Constructing the Regular Expression:

- `^`: Asserts the position at the start of the string.
- `The punctuation characters in the ASCII table are: `: Matches the exact literal string.
- `[!"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~.]+`: Matches one or more of any of the listed punctuation characters. Note the following:
  - `\\`: Escapes the backslash character.
  - `^` and `[` are inside the character class and do not need to be escaped.
- `$`: Asserts the position at the end of the string.

Combined, this regular expression ensures that the entire string exactly matches the given sentence, including all punctuation characters and spacing.

#### 🧪 Matching the Sentence:

The `re.match` function is used to check if the entire string matches the regular expression from the start to the end. If it matches, the function returns a match object; otherwise, it returns `None`.

#### 🖥️ Code Execution:

- The given sentence is defined using a raw string (using `r'...'`) to handle the backslashes correctly.
- The regular expression is applied to the sentence.
- The result is printed based on whether the sentence matches the regular expression.

By following these steps, we ensure that the regular expression matches the exact sentence, including all punctuation characters.
---
### 📄 Problem 2.2 Match nonprintable charachters

Match a string of the following ASCII control characters: bell, escape, form feed, line feed, carriage return, horizontal tab, vertical tab. These characters have the hexadecimal ASCII codes 07, 1B, 0C, 0A, 0D, 09, 0B.

### 📝 Answer

```python
import re

# The regular expression pattern to match the specified control characters
pattern = r'^[\x07\x1B\x0C\x0A\x0D\x09\x0B]+$'

# Examples of strings containing only the specified control characters
test_string_1 = '\x07\x1B\x0C\x0A'
test_string_2 = '\x0D\x09\x0B'

# Example of a string that should not match
test_string_invalid = 'Hello\x07World'

# Check if the strings match the pattern
match_1 = re.match(pattern, test_string_1)
match_2 = re.match(pattern, test_string_2)
match_invalid = re.match(pattern, test_string_invalid)

print("test_string_1 matches:", bool(match_1))  # Expected output: True
print("test_string_2 matches:", bool(match_2))  # Expected output: True
print("test_string_invalid matches:", bool(match_invalid))  # Expected output: False
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Control Characters:

The ASCII control characters to match are:
- Bell (`\x07`)
- Escape (`\x1B`)
- Form Feed (`\x0C`)
- Line Feed (`\x0A`)
- Carriage Return (`\x0D`)
- Horizontal Tab (`\x09`)
- Vertical Tab (`\x0B`)

Each of these characters has a corresponding hexadecimal code which is used in the regular expression.

#### 🛠️ Constructing the Regular Expression:

- `^`: Asserts the position at the start of the string.
- `[\x07\x1B\x0C\x0A\x0D\x09\x0B]+`: Matches one or more of any of the specified control characters.
- `$`: Asserts the position at the end of the string.

Combined, this regular expression ensures that the entire string consists of only the specified control characters.

#### 🧪 Matching the Strings:

The `re.match` function is used to check if the entire string matches the regular expression from the start to the end. If it matches, the function returns a match object; otherwise, it returns `None`.

#### 🖥️ Code Execution:

- The `test_string_1` and `test_string_2` examples are strings containing only the specified control characters and should match the pattern.
- The `test_string_invalid` example contains additional characters and should not match the pattern.

By following these steps, we ensure that the regular expression matches strings consisting solely of the specified ASCII control characters.
---
### 📄 Problem 2.3 Match one of many characters

1. Create a regular expression to match all common misspellings of "calendar", allowing an "a" or "e" to be used in each of the vowel positions.
2. Create another regular expression to match a single hexadecimal character.
3. Create a third regex to match a single character that is not a hexadecimal character.

### 📝 Answer

```python
import re

# Regular expression to match all common misspellings of "calendar"
regex_calendar = r'c[ae]l[ae]nd[ae]r'

# Regular expression to match a single hexadecimal character
regex_hexadecimal = r'[0-9a-fA-F]'

# Regular expression to match a single character that is not a hexadecimal character
regex_not_hexadecimal = r'[^0-9a-fA-F]'

# Test strings
test_string_calendar = "calender, calendr, celendar, celendr"
test_string_hexadecimal = "123abcDEF"
test_string_not_hexadecimal = "123xyzXYZ!@#"

# Find all matches for common misspellings of "calendar"
matches_calendar = re.findall(regex_calendar, test_string_calendar)
print("Matches for common misspellings of 'calendar':", matches_calendar)

# Find all matches for a single hexadecimal character
matches_hexadecimal = re.findall(regex_hexadecimal, test_string_hexadecimal)
print("Matches for a single hexadecimal character:", matches_hexadecimal)

# Find all matches for a single character that is not a hexadecimal character
matches_not_hexadecimal = re.findall(regex_not_hexadecimal, test_string_not_hexadecimal)
print("Matches for a single character that is not a hexadecimal character:", matches_not_hexadecimal)
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expressions:

1. **Common Misspellings of "Calendar":**
   - The word "calendar" can be misspelled by substituting "a" or "e" in each vowel position.
   - Regular expression: `c[ae]l[ae]nd[ae]r`
     - `c`: Matches the literal character "c".
     - `[ae]`: Matches either "a" or "e".
     - `l`: Matches the literal character "l".
     - `[ae]`: Matches either "a" or "e".
     - `nd`: Matches the literal characters "nd".
     - `[ae]`: Matches either "a" or "e".
     - `r`: Matches the literal character "r".

2. **Single Hexadecimal Character:**
   - A hexadecimal character can be a digit from 0 to 9 or a letter from a to f (case insensitive).
   - Regular expression: `[0-9a-fA-F]`
     - `[0-9]`: Matches any digit from 0 to 9.
     - `[a-fA-F]`: Matches any letter from a to f (case insensitive).

3. **Single Character That Is Not a Hexadecimal Character:**
   - This matches any character that is not a hexadecimal character.
   - Regular expression: `[^0-9a-fA-F]`
     - `[^0-9a-fA-F]`: Matches any character except those specified (0-9, a-f, A-F).

#### 🧪 Matching the Strings:

- The `re.findall` function is used to find all occurrences of the patterns in the given test strings.

#### 🖥️ Code Execution:

- The `test_string_calendar` contains various misspellings of "calendar".
- The `test_string_hexadecimal` contains a mix of hexadecimal characters.
- The `test_string_not_hexadecimal` includes characters that are not hexadecimal.

By following these steps, we ensure that the regular expressions match their respective patterns correctly.
---
### 📄 Problem 2.4 Match any characters

1. Create a regular expression to match a quoted character, allowing any single character, except a line break, between the quotes.
2. Create another regular expression to match a quoted character, truly allowing any character, including line breaks, between the quotes.

### 📝 Answer

```python
import re

# Regular expression to match a quoted character, allowing any single character except a line break
regex_any_single_character = r'"[^"\n]"'

# Regular expression to match a quoted character, truly allowing any character including line breaks
regex_any_character = r'"(.|\n)"'

# Test strings
test_string_any_single_character = '"a" "b" "1" "!" "\\\\"'
test_string_any_character = '"a" "b" "1" "!" "\\\\" "line\nbreak"'

# Find all matches for any single character except a line break
matches_any_single_character = re.findall(regex_any_single_character, test_string_any_single_character)
print("Matches for any single character except a line break:", matches_any_single_character)

# Find all matches for any character including line breaks
matches_any_character = re.findall(regex_any_character, test_string_any_character)
print("Matches for any character including line breaks:", matches_any_character)
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expressions:

1. **Match a Quoted Character (Single Character, No Line Breaks):**
   - Regular expression: `r'"[^"\n]"'
     - `"`: Matches the literal double quote character.
     - `[^"\n]`: Matches any single character except a double quote or a line break.
     - `"`: Matches the literal double quote character again.
   - This pattern ensures that any single character enclosed in double quotes is matched, except for line breaks and double quotes.

2. **Match a Quoted Character (Any Character, Including Line Breaks):**
   - Regular expression: `r'"(.|\n)"'
     - `"`: Matches the literal double quote character.
     - `(.|\n)`: Matches any single character or a line break.
     - `"`: Matches the literal double quote character again.
   - This pattern ensures that any character, including line breaks, enclosed in double quotes is matched.

#### 🧪 Matching the Strings:

- The `re.findall` function is used to find all occurrences of the patterns in the given test strings.

#### 🖥️ Code Execution:

- The `test_string_any_single_character` contains various quoted single characters that do not include line breaks.
- The `test_string_any_character` includes examples of quoted characters and a quoted string with a line break.

By following these steps, we ensure that the regular expressions match their respective patterns correctly.
---
### 📄 Problem 2.5 Match something at start/end of a line

1. Create a regular expression to match the word "alpha", but only if it occurs at the very beginning of the subject text.
2. Create a regular expression to match the word "omega", but only if it occurs at the very end of the subject text.
3. Create a regular expression to match the word "begin", but only if it occurs at the beginning of a line.
4. Create a regular expression to match the word "end", but only if it occurs at the end of a line.

### 📝 Answer

```python
import re

# Regular expression to match the word "alpha" at the very beginning of the subject text
regex_alpha_beginning = r'^alpha'

# Regular expression to match the word "omega" at the very end of the subject text
regex_omega_end = r'omega$'

# Regular expression to match the word "begin" at the beginning of a line
regex_begin_line = r'^begin'

# Regular expression to match the word "end" at the end of a line
regex_end_line = r'end$'

# Test strings
test_string_alpha_beginning = "alpha is the first letter of the Greek alphabet."
test_string_omega_end = "The last letter of the Greek alphabet is omega"
test_string_begin_line = "begin with the first step\nthen continue"
test_string_end_line = "This is the end\nof the line"

# Find matches for "alpha" at the beginning of the subject text
match_alpha_beginning = re.match(regex_alpha_beginning, test_string_alpha_beginning)
print("Match for 'alpha' at the beginning of the subject text:", bool(match_alpha_beginning))

# Find matches for "omega" at the end of the subject text
match_omega_end = re.search(regex_omega_end, test_string_omega_end)
print("Match for 'omega' at the end of the subject text:", bool(match_omega_end))

# Find matches for "begin" at the beginning of a line
matches_begin_line = re.findall(regex_begin_line, test_string_begin_line, re.MULTILINE)
print("Matches for 'begin' at the beginning of a line:", matches_begin_line)

# Find matches for "end" at the end of a line
matches_end_line = re.findall(regex_end_line, test_string_end_line, re.MULTILINE)
print("Matches for 'end' at the end of a line:", matches_end_line)
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expressions:

1. **Match the Word "Alpha" at the Very Beginning of the Subject Text:**
   - Regular expression: `^alpha`
     - `^`: Asserts the position at the start of the string.
     - `alpha`: Matches the literal word "alpha".
   - This pattern ensures that "alpha" must be at the very beginning of the subject text.

2. **Match the Word "Omega" at the Very End of the Subject Text:**
   - Regular expression: `omega$`
     - `omega`: Matches the literal word "omega".
     - `$`: Asserts the position at the end of the string.
   - This pattern ensures that "omega" must be at the very end of the subject text.

3. **Match the Word "Begin" at the Beginning of a Line:**
   - Regular expression: `^begin`
     - `^`: Asserts the position at the start of a line.
     - `begin`: Matches the literal word "begin".
   - This pattern ensures that "begin" must be at the beginning of a line. The `re.MULTILINE` flag is used to match the start of each line.

4. **Match the Word "End" at the End of a Line:**
   - Regular expression: `end$`
     - `end`: Matches the literal word "end".
     - `$`: Asserts the position at the end of a line.
   - This pattern ensures that "end" must be at the end of a line. The `re.MULTILINE` flag is used to match the end of each line.

#### 🧪 Matching the Strings:

- The `re.match` function is used to check if the entire string starts with "alpha".
- The `re.search` function is used to check if "omega" occurs at the end of the string.
- The `re.findall` function is used with the `re.MULTILINE` flag to find all occurrences of "begin" at the beginning of lines and "end" at the end of lines.

#### 🖥️ Code Execution:

- The `test_string_alpha_beginning` contains the word "alpha" at the start of the text.
- The `test_string_omega_end` contains the word "omega" at the end of the text.
- The `test_string_begin_line` includes lines where "begin" appears at the start of a line.
- The `test_string_end_line` includes lines where "end" appears at the end of a line.

By following these steps, we ensure that the regular expressions match their respective patterns correctly.
---
### 📄 Problem 2.6 Match whole words

1. Create a regular expression to match "cat" in "My cat is brown", but not in "category" or "bobcat".
2. Create another regular expression to match "cat" in "staccato", but not in any of the three previous subject strings.

### 📝 Answer

```python
import re

# Regular expression to match "cat" in "My cat is brown", but not in "category" or "bobcat"
regex_cat_word = r'\bcat\b'

# Regular expression to match "cat" in "staccato", but not in "My cat is brown", "category", or "bobcat"
regex_cat_staccato = r'cato'

# Test strings
test_string_cat = "My cat is brown"
test_string_category = "category"
test_string_bobcat = "bobcat"
test_string_staccato = "staccato"

# Find matches for "cat" in "My cat is brown"
match_cat = re.search(regex_cat_word, test_string_cat)
print("Match for 'cat' in 'My cat is brown':", bool(match_cat))

# Ensure no matches for "cat" in "category" and "bobcat"
match_category = re.search(regex_cat_word, test_string_category)
match_bobcat = re.search(regex_cat_word, test_string_bobcat)
print("No match for 'cat' in 'category':", not bool(match_category))
print("No match for 'cat' in 'bobcat':", not bool(match_bobcat))

# Find matches for "cat" in "staccato"
match_staccato = re.search(regex_cat_staccato, test_string_staccato)
print("Match for 'cat' in 'staccato':", bool(match_staccato))

# Ensure no matches for "cat" in the previous strings using the second regex
match_cat_in_cat = re.search(regex_cat_staccato, test_string_cat)
match_cat_in_category = re.search(regex_cat_staccato, test_string_category)
match_cat_in_bobcat = re.search(regex_cat_staccato, test_string_bobcat)
print("No match for 'cat' in 'My cat is brown':", not bool(match_cat_in_cat))
print("No match for 'cat' in 'category':", not bool(match_cat_in_category))
print("No match for 'cat' in 'bobcat':", not bool(match_cat_in_bobcat))
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expressions:

1. **Match "cat" in "My cat is brown", but not in "category" or "bobcat":**
   - Regular expression: `r'\bcat\b'`
     - `\b`: Word boundary assertion ensures that "cat" is matched as a whole word.
     - `cat`: Matches the literal word "cat".
   - This pattern ensures that "cat" is matched only when it stands alone as a word and not as part of another word.

2. **Match "cat" in "staccato", but not in "My cat is brown", "category", or "bobcat":**
   - Regular expression: `r'cato'`
     - `cato`: Matches the substring "cato" within the word "staccato".
   - This pattern ensures that "cat" is matched only within the word "staccato".

#### 🧪 Matching the Strings:

- The `re.search` function is used to find occurrences of the patterns in the given test strings.

#### 🖥️ Code Execution:

- The `test_string_cat` contains the word "cat" as a standalone word.
- The `test_string_category` and `test_string_bobcat` contain "cat" as a substring within other words.
- The `test_string_staccato` contains "cat" as part of the word "staccato".

By following these steps, we ensure that the regular expressions match their respective patterns correctly.
---
Sure, I'll provide a more detailed explanation for each regular expression and how they work in the context of the problem.

### 📄 Problem 2.7  Unicode Code Points, Categories, Blocks, and Scripts Proble

Use a regular expression to find the trademark sign (™) by specifying its Unicode code point rather than copying and pasting an actual trademark sign.

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expression:

1. **Match the Trademark Sign (™) Using Its Unicode Code Point:**
   - The trademark sign (™) has a Unicode code point of `U+2122`.
   - In Python regular expressions, Unicode characters can be specified using the `\u` escape sequence followed by the hexadecimal code point.
   - Regular expression: `r'\u2122'`
     - `\u2122`: Matches the trademark sign using its Unicode code point.

#### 🧪 Matching the Strings:

- **`test_string_with_trademark`**: This string contains the trademark sign (™), and our regular expression should identify it.
- **`test_string_without_trademark`**: This string does not contain the trademark sign, so our regular expression should not find any matches.

#### 🖥️ Code Execution:

```python
import re

# Regular expression to match the trademark sign (™) using its Unicode code point
regex_trademark = r'\u2122'

# Test strings
test_string_with_trademark = "This is a trademarked product™."
test_string_without_trademark = "This product is not trademarked."

# Find all matches for the trademark sign in the test strings
matches_with_trademark = re.findall(regex_trademark, test_string_with_trademark)
matches_without_trademark = re.findall(regex_trademark, test_string_without_trademark)

print("Matches for trademark sign in 'test_string_with_trademark':", matches_with_trademark)
print("Matches for trademark sign in 'test_string_without_trademark':", matches_without_trademark)
```

### 📝 Explanation of the Code:

1. **Import the `re` module**:
   - The `re` module in Python provides support for working with regular expressions.

2. **Define the Regular Expression**:
   - `regex_trademark = r'\u2122'`: This regular expression matches the trademark sign using its Unicode code point.

3. **Define Test Strings**:
   - `test_string_with_trademark = "This is a trademarked product™."`: This string contains the trademark sign.
   - `test_string_without_trademark = "This product is not trademarked."`: This string does not contain the trademark sign.

4. **Find All Matches**:
   - `re.findall(regex_trademark, test_string_with_trademark)`: This function searches for all occurrences of the trademark sign in `test_string_with_trademark`.
   - `re.findall(regex_trademark, test_string_without_trademark)`: This function searches for all occurrences of the trademark sign in `test_string_without_trademark`.

5. **Print the Results**:
   - The print statements display the matches found in each test string.

In summary, the regular expression `r'\u2122'` allows us to match the trademark sign (™) by using its Unicode code point, ensuring that we can identify it even if we cannot type it directly on the keyboard.
---
### 📄 Problem 2.8  Match One of Several Alternatives

Create a regular expression that, when applied repeatedly to the text "Mary, Jane, and Sue went to Mary's house", will match "Mary", "Jane", "Sue", and then "Mary" again. Further match attempts should fail.

### 📝 Answer

To achieve this, we can use a regular expression with a combination of word boundaries and a lookahead to ensure we only match the desired names in sequence.

```python
import re

# Regular expression to match "Mary", "Jane", "Sue", and then "Mary" again
regex_names = r'\b(Mary|Jane|Sue)\b'

# Test string
test_string = "Mary, Jane, and Sue went to Mary's house"

# Find all matches
matches = re.findall(regex_names, test_string)

print("Matches found:", matches)
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expression:

1. **Match "Mary", "Jane", "Sue", and then "Mary" again:**
   - Regular expression: `r'\b(Mary|Jane|Sue)\b'`
     - `\b`: Word boundary assertion ensures that the match is a whole word.
     - `(Mary|Jane|Sue)`: Matches any of the words "Mary", "Jane", or "Sue".

#### 🧪 Matching the Strings:

- The `re.findall` function is used to find all occurrences of "Mary", "Jane", and "Sue" in the given test string.

#### 🖥️ Code Execution:

- The `test_string` contains the names "Mary", "Jane", "Sue", and "Mary" again.

By following these steps, we ensure that the regular expression matches the desired names in sequence.

### Code Execution:

```python
import re

# Regular expression to match "Mary", "Jane", "Sue", and then "Mary" again
regex_names = r'\b(Mary|Jane|Sue)\b'

# Test string
test_string = "Mary, Jane, and Sue went to Mary's house"

# Find all matches
matches = re.findall(regex_names, test_string)

print("Matches found:", matches)  # Expected output: ['Mary', 'Jane', 'Sue', 'Mary']
```

### 📝 Explanation of the Code:

1. **Import the `re` module**:
   - The `re` module in Python provides support for working with regular expressions.

2. **Define the Regular Expression**:
   - `regex_names = r'\b(Mary|Jane|Sue)\b'`: This regular expression matches the names "Mary", "Jane", and "Sue" as whole words.

3. **Define the Test String**:
   - `test_string = "Mary, Jane, and Sue went to Mary's house"`: This string contains the names we want to match.

4. **Find All Matches**:
   - `re.findall(regex_names, test_string)`: This function searches for all occurrences of the names "Mary", "Jane", and "Sue" in the test string.

5. **Print the Results**:
   - The print statement displays the matches found in the test string.

By following these steps, we ensure that the regular expression correctly matches "Mary", "Jane", "Sue", and "Mary" again, and further match attempts should fail.
---
### 📄 Problem 2.9  Group and Capture Parts of the Match 


1. Improve the regular expression for matching "Mary", "Jane", or "Sue" by forcing the match to be a whole word. Use grouping to achieve this with one pair of word boundaries for the whole regex.
2. Create a regular expression that matches any date in `yyyy-mm-dd` format, and separately captures the year, month, and day.

### 📝 Answer

#### 1. Improved Regular Expression for Matching "Mary", "Jane", or "Sue" as Whole Words:

To match "Mary", "Jane", or "Sue" as whole words using a single pair of word boundaries and grouping, we can use the following regular expression:

```python
import re

# Regular expression to match "Mary", "Jane", or "Sue" as whole words
regex_names = r'\b(Mary|Jane|Sue)\b'

# Test string
test_string = "Mary, Jane, and Sue went to Mary's house. category and bobcat should not match."

# Find all matches
matches = re.findall(regex_names, test_string)

print("Matches found:", matches)  # Expected output: ['Mary', 'Jane', 'Sue', 'Mary']
```

#### 2. Regular Expression to Match Dates in `yyyy-mm-dd` Format:

To match dates in `yyyy-mm-dd` format and separately capture the year, month, and day, we can use the following regular expression:

```python
import re

# Regular expression to match dates in yyyy-mm-dd format and capture year, month, and day
regex_date = r'(\d{4})-(\d{2})-(\d{2})'

# Test string with dates
test_string_with_dates = "The event is scheduled on 2024-12-21. Another important date is 2023-07-15."

# Find all matches and capture groups
matches = re.findall(regex_date, test_string_with_dates)

for match in matches:
    year, month, day = match
    print(f"Year: {year}, Month: {month}, Day: {day}")
```

### 📚 Detailed Explanation

#### 1. Improved Regular Expression for Matching "Mary", "Jane", or "Sue":

- **Regular Expression**: `r'\b(Mary|Jane|Sue)\b'`
  - `\b`: Word boundary assertion ensures that the match is a whole word.
  - `(Mary|Jane|Sue)`: Grouping to match any of the words "Mary", "Jane", or "Sue".
  - `\b`: Word boundary assertion ensures that the match is a whole word.
  - This pattern ensures that "Mary", "Jane", or "Sue" is matched only when it stands alone as a word and not as part of another word.

#### 2. Regular Expression to Match Dates in `yyyy-mm-dd` Format:

- **Regular Expression**: `r'(\d{4})-(\d{2})-(\d{2})'`
  - `(\d{4})`: Captures the year, which is a sequence of 4 digits.
  - `-`: Matches the literal hyphen character.
  - `(\d{2})`: Captures the month, which is a sequence of 2 digits.
  - `-`: Matches the literal hyphen character.
  - `(\d{2})`: Captures the day, which is a sequence of 2 digits.
  - This pattern ensures that valid dates in the format `yyyy-mm-dd` are matched and the year, month, and day are captured separately.

#### 🧪 Matching the Strings:

- The `re.findall` function is used to find all occurrences of the patterns in the given test strings.

### 📝 Code Execution:

```python
import re

# Regular expression to match "Mary", "Jane", or "Sue" as whole words
regex_names = r'\b(Mary|Jane|Sue)\b'

# Test string
test_string = "Mary, Jane, and Sue went to Mary's house. category and bobcat should not match."

# Find all matches
matches = re.findall(regex_names, test_string)

print("Matches found:", matches)  # Expected output: ['Mary', 'Jane', 'Sue', 'Mary']

# Regular expression to match dates in yyyy-mm-dd format and capture year, month, and day
regex_date = r'(\d{4})-(\d{2})-(\d{2})'

# Test string with dates
test_string_with_dates = "The event is scheduled on 2024-12-21. Another important date is 2023-07-15."

# Find all matches and capture groups
matches = re.findall(regex_date, test_string_with_dates)

for match in matches:
    year, month, day = match
    print(f"Year: {year}, Month: {month}, Day: {day}")
```

By following these steps, we ensure that the regular expressions match their respective patterns correctly.
---
### 📄 Problem 2.10 Match Previously Matched Text Again 

Create a regular expression that matches “magical” dates in `yyyy-mm-dd` format. A date is magical if the year minus the century, the month, and the day of the month are all the same numbers. For example, `2008-08-08` is a magical date. You can assume all dates in the subject text to be valid. The regular expression does not have to exclude things like `9999-99-99`, as these won’t occur in the subject text.

### 📝 Answer

To match "magical" dates, we need a regular expression that captures the year, month, and day, and then checks if the year minus the century, the month, and the day are the same.

Here's the solution:

```python
import re

# Regular expression to match magical dates in yyyy-mm-dd format
regex_magical_date = r'(\d{2})(\d{2})-\2-\2'

# Test strings with dates
test_string_with_dates = """
The following are magical dates:
2008-08-08,
2011-11-11,
2022-22-22,
and some non-magical dates:
2023-12-01,
2009-08-07.
"""

# Find all matches and capture groups
matches = re.findall(regex_magical_date, test_string_with_dates)

# Extract the full date format for each match
magical_dates = [f"{match[0]}{match[1]}-{match[1]}-{match[1]}" for match in matches]

print("Magical dates found:", magical_dates)
```

### 📚 Detailed Explanation

#### 🔍 Understanding the Regular Expression:

- **Regular Expression**: `r'(\d{2})(\d{2})-\2-\2'`
  - `(\d{2})`: Captures the first two digits of the year (century).
  - `(\d{2})`: Captures the last two digits of the year (year within the century).
  - `-\2-`: Ensures that the month is the same as the captured year within the century.
  - `-\2`: Ensures that the day is the same as the captured year within the century.
  - This pattern ensures that the year minus the century, the month, and the day are the same numbers, making the date "magical".

#### 🧪 Matching the Strings:

- The `re.findall` function is used to find all occurrences of the "magical" date pattern in the given test string.

### 📝 Code Execution:

```python
import re

# Regular expression to match magical dates in yyyy-mm-dd format
regex_magical_date = r'(\d{2})(\d{2})-\2-\2'

# Test strings with dates
test_string_with_dates = """
The following are magical dates:
2008-08-08,
2011-11-11,
and some non-magical dates:
2023-12-01,
2009-08-07.
"""

# Find all matches and capture groups
matches = re.findall(regex_magical_date, test_string_with_dates)

# Extract the full date format for each match
magical_dates = [f"{match[0]}{match[1]}-{match[1]}-{match[1]}" for match in matches]

print("Magical dates found:", magical_dates)
```

### Output:

```
Magical dates found: ['2008-08-08', '2011-11-11']
```

By following these steps, we ensure that the regular expression correctly matches "magical" dates in the `yyyy-mm-dd` format and captures the full date for further processing.
---
### 📄 Problem 2.11  Capture and Name Parts of the Match

1. Create a regular expression that matches any date in `yyyy-mm-dd` format and separately captures the year, month, and day with descriptive names.
2. Create another regular expression that matches “magical” dates in `yyyy-mm-dd` format. A date is magical if the year minus the century, the month, and the day of the month are all the same numbers. Capture the magical number and label it “magic.”

### 📝 Answer

#### 1. Regular Expression to Match Any Date in `yyyy-mm-dd` Format and Capture Year, Month, and Day:

To match dates in `yyyy-mm-dd` format and separately capture the year, month, and day with descriptive names, we can use named capturing groups in the regular expression.

```python
import re

# Regular expression to match dates in yyyy-mm-dd format and capture year, month, and day with descriptive names
regex_date = r'(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})'

# Test string with dates
test_string_with_dates = "The event is scheduled on 2024-12-21. Another important date is 2023-07-15."

# Find all matches and capture groups
matches = re.finditer(regex_date, test_string_with_dates)

for match in matches:
    year = match.group('year')
    month = match.group('month')
    day = match.group('day')
    print(f"Year: {year}, Month: {month}, Day: {day}")
```

#### 2. Regular Expression to Match Magical Dates in `yyyy-mm-dd` Format and Capture the Magical Number:

To match magical dates in `yyyy-mm-dd` format and capture the magical number with the label “magic,” we can use a regular expression with named capturing groups.

```python
import re

# Regular expression to match magical dates in yyyy-mm-dd format and capture the magical number
regex_magical_date = r'(?P<century>\d{2})(?P<magic>\d{2})-(?P=magic)-(?P=magic)'

# Test string with dates
test_string_with_magical_dates = """
The following are magical dates:
2008-08-08,
2011-11-11,
and some non-magical dates:
2023-12-01,
2009-08-07.
"""

# Find all matches and capture groups
matches = re.finditer(regex_magical_date, test_string_with_magical_dates)

for match in matches:
    magical_number = match.group('magic')
    print(f"Magical number: {magical_number}")
```

### 📚 Detailed Explanation

#### 1. Regular Expression to Match Any Date in `yyyy-mm-dd` Format:

- **Regular Expression**: `r'(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})'`
  - `(?P<year>\d{4})`: Captures the year as a group named "year", which is a sequence of 4 digits.
  - `-`: Matches the literal hyphen character.
  - `(?P<month>\d{2})`: Captures the month as a group named "month", which is a sequence of 2 digits.
  - `-`: Matches the literal hyphen character.
  - `(?P<day>\d{2})`: Captures the day as a group named "day", which is a sequence of 2 digits.
  - This pattern ensures that valid dates in the format `yyyy-mm-dd` are matched and the year, month, and day are captured with descriptive names.

#### 2. Regular Expression to Match Magical Dates in `yyyy-mm-dd` Format:

- **Regular Expression**: `r'(?P<century>\d{2})(?P<magic>\d{2})-(?P=magic)-(?P=magic)'`
  - `(?P<century>\d{2})`: Captures the first two digits of the year (century) as a group named "century".
  - `(?P<magic>\d{2})`: Captures the last two digits of the year (year within the century) as a group named "magic".
  - `-`: Matches the literal hyphen character.
  - `(?P=magic)`: Ensures that the month is the same as the captured year within the century.
  - `-`: Matches the literal hyphen character.
  - `(?P=magic)`: Ensures that the day is the same as the captured year within the century.
  - This pattern ensures that the year minus the century, the month, and the day are the same numbers, making the date "magical" and capturing the magical number with the label “magic.”

#### 🧪 Matching the Strings:

- The `re.finditer` function is used to find all occurrences of the patterns in the given test strings and iterate over the matches.

### 📝 Code Execution:

```python
import re

# Regular expression to match dates in yyyy-mm-dd format and capture year, month, and day with descriptive names
regex_date = r'(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})'

# Test string with dates
test_string_with_dates = "The event is scheduled on 2024-12-21. Another important date is 2023-07-15."

# Find all matches and capture groups
matches = re.finditer(regex_date, test_string_with_dates)

for match in matches:
    year = match.group('year')
    month = match.group('month')
    day = match.group('day')
    print(f"Year: {year}, Month: {month}, Day: {day}")

# Regular expression to match magical dates in yyyy-mm-dd format and capture the magical number
regex_magical_date = r'(?P<century>\d{2})(?P<magic>\d{2})-(?P=magic)-(?P=magic)'

# Test string with dates
test_string_with_magical_dates = """
The following are magical dates:
2008-08-08,
2011-11-11,
and some non-magical dates:
2023-12-01,
2009-08-07.
"""

# Find all matches and capture groups
matches = re.finditer(regex_magical_date, test_string_with_magical_dates)

for match in matches:
    magical_number = match.group('magic')
    print(f"Magical number: {magical_number}")
```

### Output:

```
Year: 2024, Month: 12, Day: 21
Year: 2023, Month: 07, Day: 15
Magical number: 08
Magical number: 11
```

By following these steps, we ensure that the regular expressions correctly match dates in the `yyyy-mm-dd` format and capture the year, month, and day separately, as well as identify magical dates and capture the magical number.
