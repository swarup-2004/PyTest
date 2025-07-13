In **pytest**, **mark annotations** (often just called “marks”) are special decorators that let you **label**, **categorize**, or **control** the behavior of your tests.

They are written like this:

```python
@pytest.mark.some_marker
def test_something():
    ...
```

These are **not required** but are super helpful for skipping, grouping, or customizing test runs.

---

## 🎯 Most Common `pytest.mark` Annotations (with simple examples)

---

### ✅ 1. `@pytest.mark.skip`

**Skip** this test completely — it won’t run.

```python
import pytest

@pytest.mark.skip(reason="Feature not implemented yet")
def test_feature_x():
    assert False  # won't be executed
```

---

### 🕒 2. `@pytest.mark.skipif`

**Skip only if a condition is true**.

```python
import sys
import pytest

@pytest.mark.skipif(sys.platform != "win32", reason="Only runs on Windows")
def test_windows_only():
    ...
```

---

### ⏳ 3. `@pytest.mark.xfail`

Mark test as **expected to fail** (e.g., for known bugs or unfinished features).

```python
import pytest

@pytest.mark.xfail(reason="Bug #123")
def test_unfinished_feature():
    assert 2 + 2 == 5  # This will fail, but pytest won't count it as a failure
```

---

### 📚 4. `@pytest.mark.parametrize`

Used to **run the same test with different data inputs**.

```python
import pytest

@pytest.mark.parametrize("a, b, expected", [
    (1, 2, 3),
    (2, 3, 5),
    (5, 5, 10),
])
def test_add(a, b, expected):
    assert a + b == expected
```

✅ This will run the same test 3 times with different values.

---

### 🏷️ 5. Custom markers (e.g. `@pytest.mark.slow`, `@pytest.mark.api`, etc.)

You can define your **own categories** like "slow", "db", "api", etc., to **group** or **filter** tests.

```python
import pytest

@pytest.mark.slow
def test_big_data_process():
    ...

@pytest.mark.api
def test_api_response():
    ...
```

Then run only one category like:

```bash
pytest -m slow
```

To make these **custom markers official**, add them to `pytest.ini`:

```ini
# pytest.ini
[pytest]
markers =
    slow: marks tests as slow
    api: marks API-related tests
```

---

### 🧪 6. `@pytest.mark.usefixtures`

Tells pytest to use a fixture without explicitly adding it to the function’s arguments.

```python
import pytest

@pytest.fixture
def setup():
    print("Setup done")

@pytest.mark.usefixtures("setup")
def test_example():
    print("Running test")
```

---

### 🧰 7. `@pytest.mark.filterwarnings`

Control or silence warnings for specific tests.

```python
import warnings
import pytest

@pytest.mark.filterwarnings("ignore::UserWarning")
def test_ignore_warning():
    warnings.warn("This is a user warning", UserWarning)
```

---

## 📝 Summary Table

| Marker                        | Purpose                                  |
| ----------------------------- | ---------------------------------------- |
| `@pytest.mark.skip`           | Skip the test always                     |
| `@pytest.mark.skipif`         | Skip if a certain condition is true      |
| `@pytest.mark.xfail`          | Mark test that is expected to fail       |
| `@pytest.mark.parametrize`    | Run same test with different inputs      |
| Custom marks                  | Categorize tests like `@pytest.mark.api` |
| `@pytest.mark.usefixtures`    | Use fixture without listing it           |
| `@pytest.mark.filterwarnings` | Handle warnings in test                  |


