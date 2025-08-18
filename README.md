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

### Adding items

Assigning to a key that doesn’t exist will make a new item:

```python
student['age'] = 21
```
⚠️ **Gotcha**: If the key already exists, the value just gets updated.

<details>
<summary>🔎 Why adding this way works</summary>
<hr> 

When you do `student['age'] = 21`, Python checks if `'age'` already exists: - If yes → update the value. - If no → create a new key-value pair.

This makes dictionaries flexible — no need for special “add” commands.

</hr> </details>

### Deleting items

Use `del` to delete:

```python
del student['age']
```

⚠️ **Gotcha**: `del` doesn’t return anything — it just deletes.

<details>
<summary>🔎 Why use <code>del</code> instead of setting to None?</summary> <hr>
  
`del student['age']` → actually removes the pair. - `student['age'] = None` → keeps the key but gives it a placeholder value.

Use del when you truly want it gone.

</hr> </details>

### Number of items

Use `len()` to count how many pairs are inside:

```python
len(student)  # 3
```

<details> <summary>🔎 Why len works on dictionaries</summary> <hr>
  
`len()` works on any container. For dictionaries, it counts how many key-value pairs exist. Behind the scenes, Python just checks how many keys are stored in the hash table. </hr> </details>

### Iterating

Bad way:

```python
for key in student:
  print(key, student[key])  # works but not clean
```

Better way:

```python
for key, val in student.items():
  print(key, val)
```

<details> <summary>🔎 Why <code>.items()</code> is better than looping keys</summary> <hr>
  
`for key in student:` only gives keys. Then you must do `student[key]` to get the value. - `for key, val in student.items():` gives both directly and is more efficient.

That’s why looping just keys is considered an “anti-pattern.”

</hr> </details>

---

🎓 **You Do**:
Make a dictionary called `where_my_things_are`.

* Keys = things you own
* Values = where you keep them
* Loop and print:

> My backpack is kept in my bedroom

---

## 4. Lists 📋

Lists are like grocery lists.

```python
colors = ['red', 'green', 'blue']
```

* They can grow, shrink, or change.
* They keep order.

⚠️ **Gotcha**: Assigning to a position that doesn’t exist → `IndexError`.

<details> <summary>🔎 Why negative indexes exist</summary> <hr>
  
Negative indexes save typing: - Instead of `colors[len(colors)-1]` → just `colors[-1]`. Python added this to make life easier for beginners and to mirror real-world thinking (“last one, second-to-last one”). </hr> </details>

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

### Accessing items

```python
print(colors[0])    # red
print(colors[-1])   # blue (last)
print(colors[-2])   # green (second to last)
```

⚠️ **Gotcha**: Negative numbers mean “count from the end.”

### Adding items

```python
colors.append('purple')     # add one
colors.extend(['orange'])   # add many
```

⚠️ **Gotcha**: `append([3,4])` adds a whole list inside your list. Use `extend()` for flattening.

### Inserting an item

```python
colors.insert(1, 'yellow')
```

<details> <summary>🔎 Why insert exists</summary> <hr>
  
Unlike `append()`, `insert()` lets you control *exactly* where the new item goes. This is useful when order matters (e.g., keeping a sorted list).

⚠️ Gotcha: Inserting at the front of long lists is slower, because Python has to “shift” everything down.

</hr> </details>

### Removing items

```python
colors.pop()        # remove last
colors.pop(1)       # remove at index
colors.remove('red') # remove first match
```

<details> <summary>🔎 Why multiple remove options exist</summary> <hr> 
  
`pop(index)` → use when you know *where* the item is. - `remove(value)` → use when you know *what* the item is.

⚠️ Gotcha:

- `pop()` returns the item (handy if you need it).

- `remove()` doesn’t return anything.

</hr> </details>

### Clearing the list

```python
colors.clear()
```

<details> <summary>🔎 Why not just reassign to []?</summary> 
<hr>

`colors = []` → makes a new empty list, but the old one still exists in memory if something else references it. - `colors.clear()` → empties the list in-place, so anything else pointing to it sees it empty too.

⚠️ Gotcha: If multiple variables reference the same list, `.clear()` affects all of them.

</hr> </details>

### Iterating

```python
for color in colors:
  print(color)
```

With index:

```python
for idx, color in enumerate(colors):
  print(idx, color)
```

<details> <summary>🔎 Why enumerate is better</summary> <hr>
  
Without `enumerate`, you’d need something clunky like: ```python for i in range(len(colors)): print(i, colors[i]) ``` `enumerate` gives both index and value cleanly, making code shorter and easier to read. </hr> </details>

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

### Accessing items

```python
print(colors[1])   # green
print(colors.index('blue'))  # 2
```

### Iteration

```python
for color in colors:
  print(color)
```

<details> <summary>🔎 Why iterate if tuples can’t change?</summary> <hr> 
  
Tuples are often used for **fixed records** (like coordinates `(x,y)`). Iterating lets you read through their values just like lists, even if you can’t edit them. </hr> </details>

### Unpacking

```python
r, g, b = colors
print(r)  # red
```

---

## 7. Slicing ✂️

Take part of a list/tuple/string.

```python
name = "Alexandria"
print(name[0:4])  # Alex
print(name[:4])   # Alex
print(name[4:])   # andria
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

## 8. Sets 🧩

A **set** is like a bag of unique items. No duplicates allowed, no order guaranteed.

```python
fruits = {'apple', 'banana', 'orange'}
```

Or:

```python
fruits = set(['apple', 'banana'])
```

### Adding

```python
fruits.add('pear')
```

<details> <summary>🔎 Why no indexes?</summary> <hr>
  
Sets are unordered → you can’t say “add at position 2.” Python doesn’t guarantee order, so `add()` just throws it in anywhere. </hr> </details>

### Removing

```python
fruits.remove('banana')
```

⚠️ **Gotcha**: Since sets are unordered, you can’t access items by index like `fruits[0]`.

<details> <summary>🔎 Why remove by value only</summary> <hr>
  
Because sets have no order or index, the *only way* to remove is by value.

⚠️ Gotcha:

`.remove(x)` → crashes if x isn’t there.

`.discard(x)` → safely does nothing if x isn’t there.

</hr> </details>

---


## 9. Summary 📝

* **Dictionaries** = key → value (like lookups)
* **Lists** = ordered, editable collections
* **Tuples** = lists that don’t change
* **List comprehensions** = shortcuts for making new lists
* **Slicing** = grab chunks of a sequence

---

## 10. Essential Questions ❓

1. Difference between a list and a tuple?
   👉 Lists can change, tuples can’t.

2. Why doesn’t `fruit.bananas` work?
   👉 Dictionaries use `[]`, not dot notation.

3. What’s happening here?

```python
one, two, three = 'abc'
```

👉 That’s **unpacking**. `two = 'b'`.
