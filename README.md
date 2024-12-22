
# 📚 Regular Expressions: A Beginner's Guide

Welcome to the world of **Regular Expressions** (regex)! This guide will introduce you to the basics of regex, a powerful tool for searching, matching, and manipulating text. Let's dive in! 🚀

---

## 🔍 What is a Regular Expression?

A **Regular Expression** is a sequence of characters that forms a search pattern. You can use it to check if a string contains a specific pattern, replace text, or extract data.

---

## 🛠️ Basic Syntax

### 1. **Literals**
- **a**: Matches the character 'a'
- **abc**: Matches the string 'abc'

### 2. **Metacharacters**
- **.**: Matches any character except newline
- **^**: Matches the start of a string
- **$**: Matches the end of a string
- **\\**: Escapes a metacharacter (e.g., `\\.` matches a dot)

### 3. **Character Classes**
- **[abc]**: Matches any character 'a', 'b', or 'c'
- **[^abc]**: Matches any character except 'a', 'b', or 'c'
- **[a-z]**: Matches any lowercase letter
- **[0-9]**: Matches any digit

### 4. **Predefined Character Classes**
- **\\d**: Matches any digit (equivalent to `[0-9]`)
- **\\D**: Matches any non-digit
- **\\w**: Matches any word character (equivalent to `[a-zA-Z0-9_]`)
- **\\W**: Matches any non-word character
- **\\s**: Matches any whitespace character
- **\\S**: Matches any non-whitespace character

---

## 🔄 Quantifiers

Quantifiers specify how many times a character or group can occur.

- **\***: Matches 0 or more times
- **+**: Matches 1 or more times
- **?**: Matches 0 or 1 time
- **{n}**: Matches exactly n times
- **{n,}**: Matches at least n times
- **{n,m}**: Matches between n and m times

---

## 🤝 Grouping and Capturing

### 1. **Grouping**
- **(abc)**: Groups the characters 'abc' as a single unit

### 2. **Capturing Groups**
- **(\\d{3})**: Captures exactly three digits

### 3. **Non-Capturing Groups**
- **(?:abc)**: Groups without capturing

---

## 🔀 Alternation and Anchors

### 1. **Alternation**
- **a|b**: Matches 'a' or 'b'

### 2. **Anchors**
- **\\b**: Matches a word boundary
- **\\B**: Matches a non-word boundary

---

## 🧩 Special Constructs

### 1. **Lookahead and Lookbehind**
- **(?=abc)**: Positive lookahead (asserts that 'abc' follows)
- **(?!abc)**: Negative lookahead (asserts that 'abc' does not follow)
- **(?<=abc)**: Positive lookbehind (asserts that 'abc' precedes)
- **(?<!abc)**: Negative lookbehind (asserts that 'abc' does not precede)

---

## 💡 Examples

### 1. **Matching an Email Address**
```regex
^[\\w.-]+@[\\w.-]+\\.[a-zA-Z]{2,6}$
```

### 2. **Matching a Phone Number (US)**
```regex
^\\(\\d{3}\\) \\d{3}-\\d{4}$
```

### 3. **Matching a URL**
```regex
https?:\\/\\/(www\\.)?[\\w.-]+\\.[a-zA-Z]{2,6}(\\/\\S*)?
```

---

## 📖 Learning Resources

- [Regex101](https://regex101.com/): An online regex tester and debugger
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions): Comprehensive guide to regular expressions in JavaScript
- [RegexOne](https://regexone.com/): Interactive regex tutorial

---

## 🎉 Conclusion

Regular expressions are incredibly powerful and versatile. With this guide, you now have the foundation to start using regex in your projects. Practice and experiment with different patterns to become a regex master! 🧙‍♂️✨

Happy coding! 💻🚀

---
