### 🧪 What is a test?

A **test** checks if something in your code is **working the way you expect**.

Imagine you build a toy car, and now you want to test if it moves when you push it. That’s what a software test does — it checks how your code behaves when you do something to it.

---

### 🧩 A test has 4 simple parts:

#### 1. **Arrange** → Get everything ready

You **set things up** for the test.

Example: You put the toy car on the floor, make sure it's charged, and point it straight.

In code: You might create an object, prepare data, or set up a fake user.

---

#### 2. **Act** → Do the thing you're testing

You **perform the action** you want to test.

Example: You **push the toy car**.

In code: This is usually calling the function you're testing.

---

#### 3. **Assert** → Check the result

You **check if the result is what you expected**.

Example: You look at the toy car and see if it moved forward.

In code: You might write something like `assert result == expected_result`.

---

#### 4. **Cleanup** → Put things back

You **clean up**, so the next test isn’t affected.

Example: You pick up the toy car and put it away so you can test something else.

In code: You might delete test data or stop any services you started.

---

### 💡 The most important parts?

* **Act** (do something)
* **Assert** (check if it worked)

**Arrange** just prepares things.
**Cleanup** just tidies up afterward.

---

### 🎯 Final Example (Python):

```python
def add(a, b):
    return a + b

def test_add():
    # Arrange
    x = 2
    y = 3
    
    # Act
    result = add(x, y)
    
    # Assert
    assert result == 5
    
    # Cleanup (not needed here, but would be if we created files or data)
```
