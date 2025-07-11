# 🔐 Enigma — Enigma Machine Simulator
<!-- <a href="https://github.com/your-username/enigma" target="_blank">
  <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Repo" />
</a> -->

**Enigma** is a Python package and CLI tool that simulates the iconic **World War II Enigma machine**. With customizable settings for rotors, ring positions, reflectors, and plugboard wiring, Enigma offers an authentic simulation experience for cryptography enthusiasts, educators, and developers.

---

## ✨ Features

- ✅ Accurate simulation of historical Enigma encoding behavior
- ✅ Support for custom rotors, initial positions, ring settings, and notches
- ✅ Plugboard (Steckerbrett) configuration for realistic signal switching
- ✅ Reflector customization (e.g., A, B, etc.)
- ✅ Easy-to-use CLI interface for terminal operation
- ✅ Adjustable verbosity for tracing detailed encoding paths
- ✅ Python class for programmatic use in scripts or teaching tools

---

## 🧪 CLI Usage

Once installed, you can encode text directly from the terminal using the `enigma` command:

```bash
enigma "HELLO" --rotors="I II III" --initial-positions="A A A" --ring-settings="01 01 01" --plugleads="HA YZ" --verbose=2
```

---

## 🛠️ CLI Options

| Argument | Type | Description | Default |
|----------|------|-------------|---------|
| `text` | `string` | Text to encode (required) | |
| `--rotors` | `string` | Rotor names (e.g., `"I II III"`) | `"I II III"` |
| `--ring-settings` | `string` | Ring settings for rotors | `"01 01 01"` |
| `--initial-positions` | `string` | Rotor start positions | `"A A A"` |
| `--notch-positions` | `string` | Override default notch positions | `None` |
| `--reflector` | `string` | Reflector type (e.g., `"B"`) | `"A"` |
| `--plugleads` | `string` | Plugboard connections (e.g., `"AB CD"`) | `None` |
| `--verbose` | `int (0-2)` | Output verbosity (0 = silent, 2 = full trace) | `1` |

---

## 🖥️ Example Output (Verbose Mode)

When `--verbose=2`, the simulator prints detailed logs including rotor setups, placements, and per-character encoding paths.

```
########################################## Rotors Settings ##########################################
----------------------------------------------------------------------------------------------------
Rotor    | Ring  | Initial Pos  | Notch        | Forward Mapping
----------------------------------------------------------------------------------------------------
I        | 1     | A (index 0 ) | Q (index 16) | EKMFLGDQVZNTOWYHXUSPAIBRCJ
...

######################################### Rotors Placement #########################################
----------------------------------------------------------------------------------------------------
Left Rotor | Current Rotor | Right Rotor
----------------------------------------------------------------------------------------------------
N/A        | I             | II
...

##################################### Characters Encoding Paths #####################################
----------------------------------------------------------------------------------------------------
INPUT: H
Plugboard (HA)  : H => A
Forward   (III) : H -> +1 => I -> wiring => Q -> -1 => Q
Forward   (II)  : Q -> +0 => Q -> wiring => Q -> -0 => Q
Forward   (I)   : Q -> +0 => Q -> wiring => X -> -0 => X
Reflector (A)   : X => H
Backward  (I)   : H -> +0 => H -> inverse wiring => P -> -0 => P
Backward  (II)  : P -> +0 => P -> inverse wiring => U -> -0 => U
Backward  (III) : U -> +1 => V -> inverse wiring => L -> -1 => K
Plugboard (N/A) : K => K
ENCODED: K
----------------------------------------------------------------------------------------------------
...(Repeated for each character)

######################################### Encoding Complete #########################################
Input String:   HELLO
Encoded String: KCUBR
####################################################################################################
```

---

## 🧩 Use Cases

- 🧑‍🏫 **Educational tool** for teaching classical cryptography
- 🧪 **Simulation and analysis** of historical encoding mechanisms
- 🛠️ **Scripting support** for bulk encoding or testing Enigma logic
- 💡 **Exploration** of rotor stepping mechanics and signal paths

---

## 🐍 Programmatic Access

In addition to the CLI, the core `Enigma` class can be imported into Python scripts for use in custom applications, Jupyter notebooks, or crypto research.

```python
from enigma import Enigma

e = Enigma(rotors=["I", "II", "III"], ring_settings=["01", "01", "01"], initial_positions=["A", "A", "A"], plugboard={"A": "H", "Y": "Z"})
cipher_text = e.encode("HELLO")
print(cipher_text)  # KCUBR
```

---

**Enigma** brings the classic encryption machine to life with modern tooling — letting you explore history and cryptography from your terminal or code editor.