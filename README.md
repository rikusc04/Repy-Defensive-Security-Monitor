# Repy-Defensive-Security-Monitor

**Overview**
- This project implements a reference monitor that oversees file operations in the **Repy Sanbox Runtime**. In addition to the default Repy behavior, the monitor adds support for a default file to be used when files are opened without explicitly being created first. The goal of this defense monitor is to enforce file-access rules and prevent potentially unauthorized or malicious actions.
- Two versions of the reference monitor are included:
  - **`reference_monitor_v1.r2py`**:
    - The original monitor used in a red-team / blue-team simulation
    - This version enforces file constraints and achieved an approximately 80% defense rate against attacks.
  - **`reference_monitor_v2.r2py`**:
    - An updated version with additional changes and improvements integrated into the monitor.
- Attack programs used to evaluate the monitor are provided in the `attack_cases/` directory.

**Repy Runtime Dependency (Required)**
- This repository **does not include the Repy runtime**.
- To run this project, you must have the following files from a Repy distribution available:
  - `repy.py`
  - `encasementlib.r2py`
  - `restrictions.default`
- These files are part of the Repy runtime and are **external dependencies**, not owned or distributed by this repository.
- The monitor and attack cases in this repository are intended to be executed **using the Repy interpreter**.

**Python Version Requirement**
- Repy requires **Python 2.7**.  
- Python 3 is **not supported**.
- This repository includes a `.python-version` file that pins the required Python runtime to **2.7.18** for users who manage Python versions with `pyenv`
- The file does not bundle Python itself; it simply declares the expected runtime version for this project.

**Running the Monitor**
- Run the monitor from the directory that contains the `repy.py` file.
- Example:
  ```bash
  python repy.py restrictions.default encasementlib.r2py reference_monitor_v2.r2py attack_cases/attackcase1.r2py
  ```
- Or, a more general example:
  ```bash
  python repy.py restrictions.default encasementlib.r2py {name_of_reference_monitor}.r2py {name_of_attack_case_directory}/{name_of_attack_case}.r2py
  ```
