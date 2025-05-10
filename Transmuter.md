You are a master C and systems programmer. Do not produce any skeleton code or any placeholder code at any given point. Make sure to heavily docuemnt and be aware of all dependencies used in the C program. I want you to convert a Python-based CLI program called `convertions.py` into a **modular, production-stable C program** with minimal dependencies and a clean structure. Here's what you need to know and follow:

---

### 📦 General Project Structure

* The project should be renamed to: **`Transmuter`**
* Root directory structure must include:

  ```
  Transmuter/
  ├── src/                  # All C source files
  │   ├── utils/            # All utility conversion implementations
  │   └── main.c            # Central CLI entry point
  ├── include/              # All header files (shared among utils and main)
  │   └── config.h          # Configuration constants/macros
  ├── Makefile              # Production-stable Makefile for building the entire project
  └── README.md             # Document how to use Transmuter
  ```

---

### 🧠 Functionality Requirements

1. **`main.c` Responsibilities:**

   * Provide a command-line interface similar to `convertions.py`.
   * Parse user input and dispatch to the appropriate utility from `src/utils/`.
   * Implement a `--version` and `--help` flag.
   * Display clean and clear usage messages and errors.

2. **Utility Modules (`src/utils/`)**
   Convert each utility Python script into a C module. Each should:

   * Be a separate `.c` file (e.g., `yamltomd.c`, `wavtomp3.c`, etc.).
   * Have an accompanying `.h` header in `include/` if reusable.
   * Follow a consistent function signature for integration with `main.c`.

3. **Configuration:**

   * All global settings (e.g., version info, constant strings) go in `include/config.h`.

---

### 🧱 C Implementation Rules

* Use **pure C** (C11 or C99 standard).
* No C++.
* Minimize third-party dependencies:

  * Use `libyaml`, `jansson`, or `yaml-cpp` only if strictly needed.
  * Avoid full multimedia libraries unless essential (e.g., `ffmpeg` via system calls or `libav` only if absolutely needed).
  * Avoid linking large frameworks (e.g., avoid Vosk, use placeholder for now with user prompt).
* Use `system()` calls only when absolutely necessary (e.g., for invoking `ffmpeg`, `sox`, etc.).

---

### 🔁 Utilities to Port

Each Python utility program you were given must be implemented in C under `src/utils/`. Below is the mapping:

| Python Script     | C Module         | Notes                                                     |
| ----------------- | ---------------- | --------------------------------------------------------- |
| `yamltomd.py`     | `yamltomd.c`     | Use libyaml or write a minimal parser.                    |
| `yamltojson.py`   | `yamltojson.c`   | Same as above.                                            |
| `wavtotext.py`    | `wavtotext.c`    | Use system call to `ffmpeg`, placeholder for Vosk.        |
| `wavtomp3.py`     | `wavtomp3.c`     | Use `ffmpeg` via `system()` or `libav` if possible.       |
| `videotoaudio.py` | `videotoaudio.c` | Extract audio using `ffmpeg`, detect input/output format. |

---

### 🧰 Makefile

* Should build all `.c` files under `src/` and `src/utils/`.
* Must link object files into one binary: `transmuter`.
* Support a `make clean` option.
* Automatically detect changes for rebuilds.

---

### 📑 Additional Notes

* Each utility must be fully modular and callable from `main.c` without circular dependencies.
* Errors must be handled gracefully (file not found, invalid format, etc.).
* Your goal is to make a **CLI toolset written in C** that replicates the Python program’s design and usability, with greater performance and stability.
  I will then feed you the contents of each converted Python utility program individually (already uploaded). You may now proceed to execute this prompt or send it to a code-generation AI. Let me know when you're ready for the next step — creating the `main.c` file and Makefile. First here is the convertion.py file.

