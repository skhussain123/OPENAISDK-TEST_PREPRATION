# What is the UV?

**UV**  is a modern, high-performance Python package manage

## Features

- Lightning-fast package installation and dependency resolution
- Compatible with existing Python tools and workflows
- Built-in virtual environment management
- Support for modern packaging standards
- Memory-efficient operation, especially for large projects

---

## Method 1: Create UV Project Using a Package

### Step 1: Install UV (create environment Automatic)

```bash
pip install uv
```

```bash
uv init --package example-pkg
```

```bash
uv run example-pkg

```


## Method 2: Create UV Project Using a Package

```bash
uv init test
```

**download library external**

```bash
uv add openai-agents
```

**run project**
```bash
uv run uv run main.py
```

| Command                         | Action                                                              |
| ------------------------------- | ------------------------------------------------------------------- |
| `uv init --package example-pkg` | Creates a project and installs the `example-pkg` Python package.    |
| `uv init example-pkg`           | Creates a folder/project named `example-pkg`, no package installed. |



### What purpose this line in python

```bash
def main():
    print("Hello from example-app!")


if __name__ == "__main__":
    main()  python me ye line q use hoti ha if __name__ == "__main__": 
```
* Python me is line ko kehte hain "main guard" ya "dunder main idiom".

###### iska kaam:
* Jab file ko direct run karte ho (python file.py), tab __name__ ki value "__main__" hoti hai → main() chalega.
* Jab file ko import karte ho (import file), tab __name__ us file ka naam hota hai, "__main__" nahi hota → main() nahi chalega.   

**main.py**
```bash
import example


def main():
    print("runnig python main file")

print("alway running main")
if "__name__"  == "main":
    main()    
```
**example.py**
```bash

def main():
    print("runnig python example file")


print("alway running")
if "__name__"  == "main":
    main()    
```        