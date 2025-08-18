# Python Containers 🐍📦

## Learning Goals 🎯

By the end of this, you should be able to:

* Use **Lists**, **Tuples**, and **Dictionaries** to store stuff
* Make quick lists with **List Comprehensions**
* Copy or grab part of a list/tuple/string with the **Slice Operator**

---

## Road Map 🗺️

1. Setup
2. Containers (what they are)
3. Dictionaries
4. Lists
5. List Comprehensions
6. Tuples
7. Slicing (Copying)
8. Summary
9. Big Questions

---

## 1. Setup ⚙️

To follow along:

* Make a new Python project on [replit](https://replit.com/)
* Call it **Python Containers**

---

## 2. Containers (the big idea) 🏠

A **container** is just a place to keep a bunch of stuff together.

👉 In JavaScript, we used **arrays** and **objects**.
👉 In Python, we mostly use:

* **Dictionaries** (like objects in JS)
* **Lists** (like arrays in JS)
* **Tuples** (like lists, but unchangeable)

---

## 3. Dictionaries 📖

Think of a **dictionary** like a real-life dictionary: you look up a **word (key)** to find its **definition (value)**.

```python
student = {
  'name': 'Maria',
  'course': 'Coding',
  'current_week': 7
}
```

### What’s cool about dictionaries?

* You can change values
* Add new ones
* Delete ones you don’t need
* Keys must be unchangeable (like numbers, strings, or tuples)

### Getting & setting values

```python
print(student['name'])   # Maria
student['name'] = 'Tina'
print(student['name'])   # Tina
```

🚫 You **can’t** use dot notation (`student.name`) like in JS.

### Avoiding errors

If you ask for a key that doesn’t exist → Python gets mad (`KeyError`).
Use `.get()` instead:

```python
print(student.get('skills'))  
# None (instead of breaking your code)
```

You can even give it a default:

```python
print(student.get('skills', {'HTML': 5}))
```

### Checking keys

```python
if 'course' in student:
  print("Student has a course!")
```

---

### Practice 📝

Make a dictionary called `where_my_things_are`.

* Keys = your stuff (like “backpack”)
* Values = where they are (like “bedroom”)
* Loop through and print:

  > My backpack is kept in the bedroom

---

## 4. Lists 📋

A **list** is just a line of items in order.
Think: **grocery list**.

```python
colors = ['red', 'green', 'blue']
```

Lists can grow, shrink, and change.

### Accessing items

```python
print(colors[0])   # red
print(colors[-1])  # blue (last one)
```

### Changing items

```python
colors[1] = 'yellow'
```

### Adding items

```python
colors.append('purple')  # adds at the end
colors.extend(['orange', 'black'])  # add many
```

### Removing items

```python
colors.remove('orange')
last = colors.pop()  # remove last and save it
```

---

### Practice 📝

1. Make a list called `scores` with at least one dictionary:

```python
{'name': 'player1', 'points': 25}
```

2. Add another score with `append()`.
3. Loop through and print:

> player1 scored 25 points

---

## 5. List Comprehensions ⚡

Fancy word for “making a list in one line.”

Without comprehension:

```python
nums = [1, 2, 3, 4]
squares = []
for n in nums:
  squares.append(n * n)
```

With comprehension:

```python
squares = [n * n for n in nums]
```

### Filtering too

```python
even_squares = [n*n for n in nums if n*n % 2 == 0]
```

---

## 6. Tuples 🎁

A **tuple** is like a list you **can’t change**.

```python
colors = ('red', 'green', 'blue')
```

Why use them?

* Safer (no one can mess with your data)
* Faster than lists
* Can be used as dictionary keys

### Cool trick: Unpacking

```python
r, g, b = colors
print(r)  # red
```

---

## 7. Slicing (Copying) ✂️

Want part of a list/tuple/string? Slice it!

```python
name = "Alexandria"
print(name[0:4])  # Alex
```

* `[:n]` → from start to n
* `[m:]` → from m to end
* `[:]` → whole thing (copy)

Also works to replace parts of a list:

```python
letters = ['a','b','x','y','d']
letters[2:4] = ['c']
print(letters)  # ['a','b','c','d']
```

---

## 8. Summary 📝

* **Dictionaries** = lookups (key → value)
* **Lists** = ordered, editable collections
* **Tuples** = lists that can’t change
* **List comprehensions** = quick one-liners for lists
* **Slicing** = grab a chunk of a sequence

---

## 9. Essential Questions ❓

1. What’s the main difference between a list and a tuple?
   👉 Lists can change, tuples can’t.

2. Why doesn’t `fruit.bananas` work?
   👉 Because dictionaries need **square brackets**: `fruit['bananas']`.

3. What’s it called when we do:

```python
one, two, three = 'abc'
```

👉 **Unpacking**.
Here, `two = 'b'`.

---
