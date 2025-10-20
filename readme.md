# 🧾 Learning YAML

This repository documents my learning journey of **YAML (Yet Another Markup Language)** - a human-friendly data serialization format often used in configuration files for tools like Docker, Kubernetes, and CI/CD pipelines.

---

## 1. Problem Statement

When working with configuration-heavy tools like Docker Compose, GitHub Actions, or Kubernetes, managing JSON files becomes hard to read and maintain. YAML solves this problem by providing a clean, indentation-based structure that is easy for humans to read and write.

---

## 2. What is YAML?

YAML is a **data representation language**, not a programming language. It is called the superset of json as every json file can be renamed as yaml but not the opposite. It represents data in a hierarchical structure using **key-value pairs**, and **indentation** to define relationships.

Example:

```yaml
name: Sujal
learning: YAML
skills:
  - Docker
  - Node.js
  - Git and Github
```

---

## 3. Basic Syntax Rules

1. Key-Value Pair:

```yaml
language: YAML
version: 1.3
```

2. Indentation Matters: Use **spaces(Hitesh sir generally prefer 2 spaces) only** (no tabs).Indentation defines hierarchy.
3. Lists:

```yaml
fruits:
  - apple
  - banana
  - mango
```
OR 
```yaml
fruits: [apple, banana, mango]
```

4. Nested Objects:

```yaml
student:
  name: Sujal
  age: 20
  subjects:
    - Maths
    - Computer Science
```

5. Comments:

```yaml
# This is a comment in YAML. YAML doesnt have multi line comments.
```

---

## 4. Scalars in YAML

Scalars are single values like strings, numbers, or booleans.

```yaml
# Strings
string1: Hello World          # Plain style
string2: "Hello & World"      # Double-quoted (allows escape characters and special symbols)
string3: 'Hello World'        # Single-quoted (treats everything literally)

# Integers and Floats
integer: 25
float: 99.9

# Booleans
bool_true1: true
bool_true2: yes # same as true
bool_true3: on # same as true
bool_false1: false
bool_false2: no # same as false
bool_false3: off # same as false

# Null values
key1: null
key2: Null
key3: NULL
key4: ~
key5:    # Empty value also means null
```

---

## 5. Multi-line Strings

You can define multi-line strings using **|** (literal) or **>** (folded):

```yaml
description: |
  This is a multi-line string.
  All new lines are preserved.

summary: >
  This is a folded string
  where newlines are converted to spaces.
```

---

## 6. Using Anchors and Aliases

Anchors (&) and Aliases (\*) let you reuse data without repetition.

```yaml
defaults: &default
  name: Sujal
  country: India

student1:
  <<: *default
  age: 21
```

Here, `student1` inherits the values from `defaults`. Very similar to pointer concept in C.

---

## 7. Explicit type conversion

```yaml
age: !!int "21"
pin_code: !!str 123456
```

## 8. Real-World Example — Docker Compose

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mongo
    ports:
      - "27017:27017"
```

This YAML defines two services - **web** and **db**  with their respective port mappings.

---

## 8. Common Mistakes to Avoid

❌ Mixing tabs and spaces\
❌ Forgetting indentation\
❌ Using `:` without a space after it

Example of wrong YAML:

```yaml
key:value   # ❌ Wrong (missing space)
```

Correct version:

```yaml
key: value   # ✅ Correct
```

---

## 9. Why YAML is Popular

- Human-readable and simple syntax
- Used in DevOps tools like Docker Compose, Kubernetes, and GitHub Actions
- Supports comments (unlike JSON)
- Easily maps to JSON

---

## Conclusion

This README covers the core YAML concepts from basics to practical examples.\
Learned and inspired by **Chai aur Code’s** amazing explanations ☕🚀

