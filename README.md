# Python Containers 🐍📦

## Learning Goals 🎯

By the end of this, you should be able to:

* Use **Lists**, **Tuples**, and **Dictionaries** to store stuff
* Make quick lists with **List Comprehensions**
* Copy or grab part of a list/tuple/string with the **Slice Operator**

---

## 1. Setup ⚙️

* Make a new Python project on [replit](https://replit.com/)
* Call it **Python Containers**

---

## 2. Containers (the big idea) 🏠

A **container** is just a place to keep a bunch of stuff together.

👉 In JavaScript we used **arrays** and **objects**.
👉 In Python we mostly use:

* **Dictionaries** (lookups, like JS objects)
* **Lists** (ordered collections, like JS arrays)
* **Tuples** (lists that can’t change)

<details>
<summary>🔎 Why Python has different containers</summary>
<hr>

Python splits containers into different “jobs”:

* **Lists** are best for ordered stuff that changes (like a to-do list).
* **Tuples** are for fixed stuff that shouldn’t change (like RGB color values).
* **Dictionaries** are for lookups, like a real dictionary (word → meaning).

This separation keeps your code **clearer** and lets Python **optimize performance** (tuples are faster because they never change).

</hr>
</details>

---

## 3. Dictionaries 📖

Think of a **dictionary** like a real dictionary: you look up a **word (key)** to find its **definition (value)**.

```python
student = {
  'name': 'Maria',
  'course': 'Coding',
  'current_week': 7
}
```

* You can change values, add new ones, or delete them.
* Keys must be **immutable** (strings, numbers, tuples).

⚠️ **Gotcha**: You can’t use lists as keys, because lists can change — that would break the lookup system.

<details>
<summary>🔎 Why keys must be immutable</summary>
<hr>

Imagine if you used a list as a key:

```python
my_dict = {[1,2]: "hello"}  # ❌
```

If you later changed that list to `[1,3]`, Python wouldn’t know where to find the value anymore. That’s why only unchangeable types (strings, numbers, tuples) are allowed.

</hr>
</details>

### Accessing values

```python
print(student['name'])   # Maria
student['name'] = 'Tina'
```

⚠️ **Gotcha**: You can’t do `student.name`. Python doesn’t let dictionaries work with dot notation because it might clash with method names (like `.items()` or `.get()`).

<details>
<summary>🔎 Why no dot notation like JS?</summary>
<hr>

In JavaScript, objects are very flexible — properties and methods live in the same space, so `obj.name` is fine.

In Python, dictionary methods (like `.get()` and `.items()`) could be confused with keys. Example:

```python
student = {"items": "something"}
print(student.items)  # Uh oh! method or data?
```

Square brackets make it unambiguous.

</hr>
</details>

---

## 4. Lists 📋

Lists are like grocery lists.

```python
colors = ['red', 'green', 'blue']
```

* They can grow, shrink, or change.
* They keep order.

⚠️ **Gotcha**: Assigning to a position that doesn’t exist → `IndexError`.

<details>
<summary>🔎 Why lists allow negative indexing</summary>
<hr>

Python made `colors[-1]` mean “last item” so you don’t have to type:

```python
colors[len(colors)-1]
```

It’s shorter and easier for beginners. Negative indexing also matches how people think of “counting from the end.”

</hr>
</details>

---

## 5. List Comprehensions ⚡

Shortcut for making lists.

Normal way:

```python
squares = []
for n in range(5):
    squares.append(n*n)
```

Comprehension way:

```python
squares = [n*n for n in range(5)]
```

<details>
<summary>🔎 Why Python uses comprehensions</summary>
<hr>

Python is built around the idea of **readable, expressive code**. A comprehension is like saying:

> “I want `n*n` for each `n` in my list.”

It matches how you’d explain it in English and makes code shorter without losing clarity.

</hr>
</details>

⚠️ **Gotcha**: If you reuse variable names inside, they overwrite outside ones.

---

## 6. Tuples 🎁

Tuples = lists you can’t change.

```python
colors = ('red', 'green', 'blue')
```

⚠️ **Gotcha**: A single-item tuple needs a comma → `(5,)`.

<details>
<summary>🔎 Why tuples exist if we already have lists</summary>
<hr>

* Tuples are **faster** because Python doesn’t have to worry about changes.
* They’re **safer**: data can’t be accidentally changed.
* They can be used as **dictionary keys**, unlike lists.

Think of them like a **locked box** versus a list, which is a **backpack you can add/remove from anytime**.

</hr>
</details>

---

## 7. Slicing ✂️

Take part of a list/tuple/string.

```python
name = "Alexandria"
print(name[0:4])  # Alex
```

⚠️ **Gotcha**: Slice end index is **exclusive**. `[0:4]` gives indices 0,1,2,3.

<details>
<summary>🔎 Why slice end index is exclusive</summary>
<hr>

This makes it easy to see how big your slice is:

```python
letters[2:5]  # has 3 items (5-2 = 3)
```

It also plays nice with zero-based indexing and loops.

</hr>
</details>

👉 Pro Tip: `[:]` makes a full copy of a list. This is often safer than assigning one list to another.

---

## 8. Summary 📝

* **Dictionaries** = key → value (like lookups)
* **Lists** = ordered, editable collections
* **Tuples** = lists that don’t change
* **List comprehensions** = shortcuts for making new lists
* **Slicing** = grab chunks of a sequence

---

## 9. Essential Questions ❓

1. Difference between a list and a tuple?
   👉 Lists can change, tuples can’t.

2. Why doesn’t `fruit.bananas` work?
   👉 Dictionaries use `[]`, not dot notation.

3. What’s happening here?

```python
one, two, three = 'abc'
```

👉 That’s **unpacking**. `two = 'b'`.
