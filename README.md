# Transparent Mode

A Python code visualizer that shows variable values, loop iterations, and condition results **inline in your editor** — no debugger, no console, no guessing.

![Transparent Mode in action](https://i.imgur.com/placeholder.png)

## What it does

Click **Transparent** and ghost annotations appear directly beside each line of your code:

```python
numbers = [4, 7, 2, 9, 1]     # // numbers = [4, 7, 2, 9, 1]
total = 0                       # // total = 0
for num in numbers:             # // 5 iterations   4 → 7 → 2 → 9 → 1
    total = total + num         # // total = 23
average = total / len(numbers)  # // average = 4.6
is_above_five = average > 5     # // is_above_five = False
```

Every annotation shows the value **after** that line executed — not before, not at the end of the program. Just exactly what that line did.

## Features

- **Inline overlays** — values appear beside each line, not in a separate panel
- **Loop visualization** — see every iteration value in a single `4 → 7 → 2 → 9 → 1` flow
- **Condition results** — `if`/`elif` lines show `TRUE ✓` or `FALSE ✗` with the loop variable that triggered it (e.g. `FALSE ✗ (n=3)`)
- **Assignment tracking** — only shows what each line actually changed, not the entire program state
- **5 built-in examples** — Average calculator, Fibonacci, FizzBuzz, Bubble sort, Password checker
- **Runs entirely in the browser** — no server, no install, powered by [Pyodide](https://pyodide.org) (Python via WebAssembly)

## How to use

1. Open `index.html` in Chrome (or visit the live site)
2. Write or paste Python code in the editor
3. Click **▶ Run** to execute normally and see output
4. Click **◈ Transparent** to see inline annotations
5. Click **Clear** to reset

## Why this exists

Every other Python visualizer makes you step through code line by line, or shows execution in a separate panel. Transparent Mode puts the values exactly where you're already looking — beside the code itself. It's the closest thing to being able to *see through* your program as it runs.

Inspired by [Quokka.js](https://quokkajs.com) for JavaScript, but for Python, in the browser, with no install required.

## Tech stack

- **Editor** — plain `<textarea>` with an absolutely-positioned overlay div
- **Python runtime** — [Pyodide](https://pyodide.org) (CPython compiled to WebAssembly)
- **Tracer** — `sys.settrace` with a delayed-write pattern to capture post-execution state
- **No frameworks, no build step** — single `index.html` file

## Running locally

Just open `index.html` in Chrome. That's it.

```bash
open index.html
```

Pyodide loads from CDN on first use (~10MB). After that it's cached by the browser.

## Limitations (alpha)

- **List comprehensions** — annotations may not show inside comprehensions
- **Functions** — variables inside function calls are not currently traced
- **Long lines** — annotations push off-screen if code lines are very long
- Works best in **Chrome** (Pyodide performance varies in other browsers)

## License

MIT
