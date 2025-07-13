## ✅ **1. Set up your project the right way**

### 🧪 Use a virtual environment

* Use `venv` to **create a separate Python environment** for your project so it doesn’t mess with your system Python.
* Install everything you need using:

  ```bash
  pip install -e .  # For your package in editable mode
  pip install pytest  # For testing
  ```

---

## 📦 **2. Create a `pyproject.toml` file**

This is like the "project settings" file.

Example:

```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[project]
name = "your_project_name"
version = "0.1.0"
```

This tells tools how to build your project.

---

## 🧪 **3. Write your tests**

### 🔍 How pytest finds your tests:

* Looks for files like `test_*.py` or `*_test.py`
* Looks inside those files for:

  * Functions starting with `test_`
  * Classes starting with `Test` (no `__init__` method)
  * Functions inside those classes also starting with `test_`

---

## 🧱 **4. Organize your files properly**

### 🗂️ Recommended folder structure:

```
pyproject.toml
src/
    mypkg/
        __init__.py
        app.py
        view.py
tests/
    test_app.py
    test_view.py
```

This is called the **src layout**. It:

* Keeps your test code separate from your actual app code
* Prevents weird import bugs
* Works well with `pip install -e .`

---

## 🧪 **5. Configure pytest properly**

In `pyproject.toml`, tell pytest to use **importlib** mode (which is cleaner and newer):

```toml
[tool.pytest.ini_options]
addopts = [
    "--import-mode=importlib"
]
```

This makes sure imports work correctly and prevents duplicate imports or path issues.

---

## 🧼 **6. Want to cleanly test installed packages?**

If you don't use `-e`, tell Python to look in the right place for your code:

```bash
PYTHONPATH=src pytest
```

Or permanently in `pyproject.toml`:

```toml
[tool.pytest.ini_options]
pythonpath = "src"
```

---

## 🧪 **7. Putting tests inside your package**

You can also do this:

```
src/
    mypkg/
        app.py
        view.py
        tests/
            test_app.py
            test_view.py
```

Then run tests like:

```bash
pytest --pyargs mypkg
```

This works too — it’s up to you which style you prefer.

---

## 🚨 **8. Avoid these mistakes**

* Don't use `python setup.py test` — it's outdated and might break in future.
* Don't use `pytest-runner` — it’s deprecated.
* Use `tox` instead if you want to **test your package in multiple environments** automatically.

---

## ✅ **9. Style check with flake8-pytest-style**

This tool helps you catch mistakes in test code like:

* Wrong names
* Wrong usage of `@pytest.fixture`
* Bad formatting

Install it with:

```bash
pip install flake8 flake8-pytest-style
```

---

## 🧠 Final Takeaway

If you're starting a new Python project with tests:

1. Use a virtual environment.
2. Use `pytest` for writing and running tests.
3. Use a `src/` layout and `pyproject.toml` for clean structure.
4. Install your package with `pip install -e .`
5. Use `--import-mode=importlib` to avoid headaches.
6. Use `flake8-pytest-style` for good test style.


