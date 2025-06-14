# trSrt-PyPI-package
Python package to solve Turkish characters conversion problem 

# 🇹🇷 trStr — Turkish-Aware String Casing

**`trStr`** is a lightweight but powerful Python utility that solves the long-standing issue of incorrect string casing for Turkish characters — especially the problematic conversions between **“i” ↔ “İ”** and **“I” ↔ “ı”**.

[![PyPI version](https://badge.fury.io/py/trstr.svg)](https://pypi.org/project/trstr/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## ❗ The Problem

Python's built-in string methods like `.upper()`, `.lower()`, `.title()`, and `.capitalize()` are designed with the English alphabet in mind. This creates serious issues when dealing with Turkish text, especially the letters **“i”** and **“I”**, which have unique uppercase/lowercase mappings in Turkish:

```python
"aliler bize geldi".upper()
# Output: 'ALILER BIZE GELDI' ❌
# Expected: 'ALİLER BİZE GELDİ' ✅
```

Another example:

```python
"Istanbul".lower()
# Output: 'istanbul' ❌
# Expected: 'ıstanbul' ✅
```

These small mismatches can break user interfaces, search features, sorting logic, and more — especially in applications that rely on proper Turkish linguistic rules.

---

## ✅ The Solution: `trStr`

`trStr` is a custom string class that wraps your original string and overrides Python's core casing methods to apply **Turkish-aware transformations**.

With `trStr`, you can safely perform:

- `.lower()` → converts `I` to `ı`, and keeps `i` as `i`
- `.upper()` → converts `i` to `İ`, and `ı` to `I`
- `.capitalize()` → capitalizes first character in a Turkish-correct way
- `.title()` → capitalizes each word with proper `i/İ` handling

---

## 🧪 Usage Example

```python
from trstr import trStr

text = trStr("aliler bize geldi")

print(text.upper())      # ALİLER BİZE GELDİ
print(text.lower())      # aliler bize geldi
print(text.capitalize()) # Aliler bize geldi
print(text.title())      # Aliler Bize Geldi
```

All output will now match proper Turkish grammar, regardless of the system locale or platform.

---

## 🚀 Installation

You can install the package via PyPI:

```bash
pip install trstr
```

---

## 📦 Internals & Behavior

`trStr` internally uses a mapping table that accounts for the following special casing rules:

| Character | Correct Turkish Upper | Correct Turkish Lower |
|-----------|-----------------------|------------------------|
| i         | İ                     | i                      |
| I         | I (en) / İ (tr)       | ı                      |
| ı         | I                     | ı                      |
| İ         | İ                     | i                      |

> Unlike `str.upper()` and `str.lower()` which rely on the system's C-locale or Unicode tables, `trStr` applies the correct Turkish casing rules explicitly — making it reliable and cross-platform.

---

## 💡 Why This Matters

In many Turkish-language applications — including forms, user names, emails, location data, and UI text — a small mistake in casing leads to:

- failed searches (`"Ali"` ≠ `"ALİ"`)
- incorrect sorting/grouping
- awkward display in user interfaces
- security/auth problems in case-insensitive string matching

With `trStr`, you can stop writing casing workarounds and let the package handle it safely and correctly.

---

## 🧑‍💻 About the Author

Developed by [Fatih Dinç](https://mfatihdinc.com)  
a software developer who got tired of `"ALILER"` being wrong 😅

Feel free to open issues, contribute, or suggest improvements.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — free to use, modify, and redistribute.

---

> ✅ Let's fix Turkish casing in Python once and for all — no more `"ALILER"` nightmares!
