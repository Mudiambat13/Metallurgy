# Installation

!!! note
    MetallurgyPy has not been published to PyPI yet. Until the owner approves and publishes a release, install from a clone of the repository (development install below). The `pip install metallurgypy` commands in this page describe installation after publication.

## Requirements

- MetallurgyPy `0.2.0.dev0` (current development version; not yet published on PyPI)
- Python 3.10 or later; CI tests Python 3.10, 3.11, 3.12 and 3.13
- Studio currently uses PySide6 6.5 to below 6.12; PySide6 6.12 can crash on process shutdown
- Windows or Linux for Studio; macOS compatibility is kept possible

## Install options

=== "Core only"

    ```bash
    pip install metallurgypy
    ```

    No PySide6 is installed. Suitable for servers and notebooks.

=== "With Studio (GUI)"

    ```bash
    pip install "metallurgypy[gui]"
    metallurgypy-studio
    ```

=== "Optional features"

    ```bash
    pip install "metallurgypy[visualization]"
    pip install "metallurgypy[excel]"          # read .xlsx files
    pip install "metallurgypy[uncertainty]"    # no extra package: uncertainty propagation is built in
    pip install "metallurgypy[all]"
    ```

## Development install

```bash
git clone https://github.com/Mudiambat13/MetallurgyPy.git
cd MetallurgyPy
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

pip install -e .                 # Core
pip install -e ".[gui]"          # Core + Studio
pip install -e ".[dev]"          # tests, lint, type checks
```

During development Studio can also be launched with:

```bash
python -m metallurgypy_studio
```

## Build this documentation locally

```bash
pip install -r docs/requirements.txt
mkdocs serve            # live preview at http://127.0.0.1:8000
mkdocs build --strict   # same check as CI
```

## Verify the installation

```bash
python -c "import metallurgypy; print(metallurgypy.__version__)"
```

To confirm that the Core really is GUI-free, check that `PySide6` is absent from a fresh Core-only environment (`pip list`).
