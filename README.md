# Password Strength & Breach Checker

A desktop app that rates how strong a password is and checks whether it has appeared in a known data breach. It runs on your own computer with a simple Tkinter window.

## Features

- Rates password strength from very weak to very strong, using the zxcvbn library
- Estimates how long the password would take to crack offline
- Checks the password against the Have I Been Pwned breach database
- Suggests specific improvements based on the analysis
- Updates the results as you type

## Requirements

- Python 3.9+
- An internet connection for the breach check. The strength rating works offline.

## Installation

```bash
git clone https://github.com/KhanLabs/Password-Strength-HIBP-Checker.git
cd Password-Strength-HIBP-Checker
pip install -r requirements.txt
```

## Usage

```bash
python main.py
```

Type a password into the field. The strength rating and crack time appear straight away. The breach check runs in the background and shows its result when it finishes.

## Building a standalone .exe

```bash
pip install pyinstaller
pyinstaller --onefile --windowed main.py
```

This produces a single executable in `dist/` that runs without a Python install.

## Privacy

The password itself never leaves your device. For the breach check, the app turns the password into a SHA-1 hash and sends only the first 5 characters of that hash to the Have I Been Pwned API. The API sends back every breached hash that starts with those characters, and the app checks for a match on your computer. This method is called k-anonymity. Neither the password nor its full hash is ever sent.

## License

MIT. See [LICENSE](LICENSE).
