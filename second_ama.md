
## Single responsibility principle in Python?
Each class or module should do one clear job.  
 If a class handles only one responsibility, it’s easier to read, test, and change later.  
A `User` class should hold user data and behaviors (like `login()`), while a separate `Logger` class should handle logging. Don’t mix both in one class.

---

## What is method overloading in Python?
 Python doesn't support classic method overloading (multiple methods with same name but different signatures) like Java.  
 Use default arguments, `*args`/`**kwargs`, or tools like `functools.singledispatch`.  
**Example:**
```py
def greet(name, greeting="Hi"):
    print(f"{greeting}, {name}")

# Works for one or two args — no separate overloaded functions needed.
greet("Kartik")
greet("Kartik", "Hello")
```

---

## Module and package difference?
**Module:** A single Python file that contains functions, classes, or variables.  
**Package:** A folder that groups many modules and usually has an `__init__.py` file. It’s how you bundle related modules together.    

---

## What is CSS `float`?
 `float` pushes an element left or right so inline content (like text) wraps around it.  
---

## Difference between `git pull` and `git fetch`?
**`git fetch`:** Downloads changes from remote branches to your local repo, but doesn't change your working files. Safe — you can inspect before merging.  
**`git pull`:** Fetches + immediately merges (or rebases) into your current branch. It's `fetch` + `merge` by default.  

---

## What is list comprehension?
A compact way to make lists from existing lists or iterables using a one-line expression.  
**Example:**  
```py
squares = [x*x for x in range(5)]        # [0, 1, 4, 9, 16]
evens = [x for x in range(10) if x%2==0] # [0, 2, 4, 6, 8]
```


---

## What are the different values for the `position` property (CSS)?
- **static:** Default — element flows normally.  
- **relative:** Keeps space in the page flow but you can shift it with `top/left/right/bottom`.  
- **absolute:** Removed from normal flow and positioned relative to the nearest positioned ancestor (one that is not `static`).  
- **fixed:** Stays in place relative to the browser window (good for sticky headers).  
- **sticky:** Acts like `relative` until scrolling passes a threshold, then it “sticks” like `fixed`.  


---

## What is `__init__` function?
`__init__` is the Python constructor — it runs when you create a new object from a class. Use it to set up attributes.  
**Example:**
```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p = Person("Ana", 25)
```

---

## Difference in `id` and `class`?

- **`id`**: should be unique on a page (one element only). Select with `#myId`. Higher CSS specificity.  
- **`class`**: reusable — many elements can share the same class. Select with `.myClass`.  
**Use:** `id` for a single special element, `class` for styling or behavior shared across multiple elements.

---

## How do you make an element unselectable in CSS?
Use the `user-select` property:
```css
.unselectable {
  user-select: none;
  -webkit-user-select: none; /* Safari/old Chrome */
  -moz-user-select: none;    /* Old Firefox */
}
```
That prevents the user from highlighting text. For older IE, there was an `unselectable="on"` attribute, but `user-select` is the standard way today.

---

## What is the difference between process and thread?
**Process:** A separate running program with its own memory space.  
**Thread:** A smaller unit inside a process that shares the process memory with other threads.  

---

## What are decorators?
A decorator is a function that wraps another function (or method) to change or extend its behavior, without modifying the wrapped function’s code. You write them with `@` above a function.  
**Simple example:**
```py
import time

def timer(fn):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = fn(*args, **kwargs)
        print("Elapsed:", time.time() - start)
        return result
    return wrapper

@timer
def work(n):
    sum(range(n))

work(1000000)  # prints elapsed time after running
```
