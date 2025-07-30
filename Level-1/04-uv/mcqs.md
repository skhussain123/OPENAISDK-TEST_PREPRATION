# MCQs on UV (Python Package and Project Manager)
## Questions

**Q1. What is uv in the context of Python?**  
a) A library for image processing  
b) A fast Python package and project manager (correct)  
c) A replacement for asyncio event loop  
d) A tool for AI model training  

**Explanation**: uv is a high-performance Python package and project manager written in Rust, designed to manage dependencies, projects, and scripts.[](https://docs.astral.sh/uv/)

---

**Q2. What does the command `uv init example` do?**  
a) Installs a Python version  
b) Creates a new project named "example" (correct)  
c) Runs a script named "example"  
d) Adds a dependency to an existing project  

**Explanation**: `uv init example` initializes a new Python project named "example" with a basic structure, including `pyproject.toml`.[](https://docs.astral.sh/uv/)

---

**Q3. What is created when you run `uv init example`?**  
a) A virtual environment only  
b) A project directory with `pyproject.toml` (correct)  
c) A script with inline metadata  
d) A new Python version  

**Explanation**: `uv init example` creates a project directory with files like `pyproject.toml` for project metadata and dependencies.[](https://docs.astral.sh/uv/)

---

**Q4. How does uv manage project dependencies?**  
a) By modifying Python’s standard library  
b) Using lockfiles and virtual environments (correct)  
c) By installing hardware drivers  
d) By generating AI prompts  

**Explanation**: uv uses lockfiles (e.g., `uv.lock`) and virtual environments to manage project dependencies consistently.[](https://docs.astral.sh/uv/)

---

**Q5. What is the purpose of the `uv add ruff` command?**  
a) To remove the ruff package  
b) To add ruff as a project dependency (correct)  
c) To run the ruff tool  
d) To install a new Python version  

**Explanation**: `uv add ruff` adds the `ruff` package as a dependency to the project’s `pyproject.toml` and installs it in the virtual environment.[](https://docs.astral.sh/uv/)

---

**Q6. What happens when you run `uv run ruff check`?**  
a) It creates a new project  
b) It runs the ruff tool in the project’s environment (correct)  
c) It installs a new Python version  
d) It generates a lockfile  

**Explanation**: `uv run ruff check` executes the `ruff check` command in the project’s virtual environment, ensuring dependencies are available.[](https://docs.astral.sh/uv/)

---

**Q7. What is the role of the `uv.lock` file in a uv project?**  
a) It stores project source code  
b) It contains exact dependency versions (correct)  
c) It defines Python version settings  
d) It runs scripts automatically  

**Explanation**: The `uv.lock` file is a lockfile that stores exact versions of project dependencies for reproducible installations.[](https://docs.astral.sh/uv/guides/projects/)

---

**Q8. What does the `uv sync` command do?**  
a) Creates a new script  
b) Installs dependencies from the lockfile (correct)  
c) Runs a Python script  
d) Updates Python versions  

**Explanation**: `uv sync` installs all dependencies listed in `uv.lock` to ensure the project environment matches the lockfile.[](https://docs.astral.sh/uv/)

---

**Q9. How does uv handle single-file scripts?**  
a) By requiring a manual virtual environment  
b) By managing dependencies with inline metadata (correct)  
c) By avoiding dependency management  
d) By installing new Python versions  

**Explanation**: uv manages script dependencies using inline metadata in the script file, running them in isolated virtual environments.[](https://docs.astral.sh/uv/)

---

**Q10. What does the command `uv add --script example.py requests` do?**  
a) Runs the `example.py` script  
b) Adds the `requests` package to `example.py` metadata (correct)  
c) Creates a new project named `example`  
d) Installs a new Python version  

**Explanation**: `uv add --script example.py requests` updates `example.py` with inline metadata to include `requests` as a dependency.[](https://docs.astral.sh/uv/)

---

**Q11. What happens when you run `uv run example.py`?**  
a) It creates a new project  
b) It runs the script in an isolated virtual environment (correct)  
c) It installs a new Python version  
d) It generates a lockfile  

**Explanation**: `uv run example.py` executes the script in an isolated virtual environment, installing its dependencies as needed.[](https://docs.astral.sh/uv/)

---

**Q12. What is `uvx` in the context of uv?**  
a) A tool for AI model training  
b) An alias for `uv tool run` (correct)  
c) A command to create projects  
d) A Python version manager  

**Explanation**: `uvx` is an alias for `uv tool run`, used to run Python tools in ephemeral environments.[](https://docs.astral.sh/uv/)

---

**Q13. What does `uv tool install ruff` do?**  
a) Adds ruff to a script’s metadata  
b) Installs the ruff tool globally (correct)  
c) Runs the ruff tool  
d) Creates a new project  

**Explanation**: `uv tool install ruff` installs the `ruff` tool and its executable globally for command-line use.[](https://docs.astral.sh/uv/)

---

**Q14. How does uv support Python version management?**  
a) By modifying Python’s standard library  
b) By installing and switching Python versions (correct)  
c) By generating AI models  
d) By creating lockfiles  

**Explanation**: uv allows installing multiple Python versions and switching between them using commands like `uv python install` and `uv python pin`.[](https://docs.astral.sh/uv/)

---

**Q15. What does `uv python install 3.10 3.11 3.12` do?**  
a) Runs scripts with multiple Python versions  
b) Installs Python versions 3.10, 3.11, and 3.12 (correct)  
c) Creates a project with multiple versions  
d) Updates the `uv.lock` file  

**Explanation**: `uv python install 3.10 3.11 3.12` downloads and installs the specified Python versions.[](https://docs.astral.sh/uv/)

---

**Q16. What is the purpose of `uv python pin 3.11`?**  
a) To run a script with Python 3.11  
b) To set Python 3.11 as the project’s version (correct)  
c) To install Python 3.11 globally  
d) To create a new virtual environment  

**Explanation**: `uv python pin 3.11` sets Python 3.11 as the preferred version for the current project directory by updating `.python-version`.[](https://docs.astral.sh/uv/)

---

**Q17. What is the `uv pip` interface used for?**  
a) To generate AI prompts  
b) To replace pip and virtualenv commands (correct)  
c) To manage hardware resources  
d) To run Python scripts  

**Explanation**: The `uv pip` interface provides a faster alternative to `pip` and `virtualenv` commands, with advanced features.[](https://docs.astral.sh/uv/)

---

**Q18. What does `uv pip compile` do?**  
a) Runs a Python script  
b) Creates a platform-independent requirements file (correct)  
c) Installs a new Python version  
d) Generates a lockfile for scripts  

**Explanation**: `uv pip compile` compiles requirements into a platform-independent `requirements.txt` file for consistent installations.[](https://docs.astral.sh/uv/)

---

**Q19. How does `uv pip sync` improve dependency installation?**  
a) By avoiding virtual environments  
b) By installing dependencies from a requirements file (correct)  
c) By generating inline script metadata  
d) By running tools globally  

**Explanation**: `uv pip sync` installs dependencies from a `requirements.txt` file, ensuring the environment matches the specified versions.[](https://docs.astral.sh/uv/)

---

**Q20. Why is uv useful for agentic AI development?**  
a) It simplifies AI model training  
b) It manages dependencies for AI projects efficiently (correct)  
c) It generates AI prompts automatically  
d) It replaces asyncio event loops  

**Explanation**: uv’s fast dependency and environment management is ideal for AI projects (e.g., with FastAPI), ensuring reproducible setups for agentic systems.[](https://docs.astral.sh/uv/)
