# SE Blueprint Calculator

A **Space Engineers Blueprint Calculator for Linux**, written entirely in Bash.

If you've ever wanted to quickly determine the components required to build a Space Engineers blueprint from the Linux command line, this is for you.

## Why?

Looking for a Space Engineers Blueprint Calculator for Linux, it quickly became apparent that I wasn't going to find anything that was actually built for Linux.

So, I built one.

Along the way I discovered that knowing the **PCU cost** of a blueprint could also be useful - so naturally, that got added too.

The result is a lightweight, self-contained Bash CLI that can read your local Space Engineers blueprints and calculate their requirements without needing a separate application, database, or web service.

---

## Features

* 🔧 Calculate the required components for a blueprint
* ⚡ Calculate the blueprint's total **PCU cost**
* 🐧 Designed specifically for **Linux**
* 🎮 Automatically searches for your Steam Library
* 📁 Automatically locates your local Space Engineers Blueprint collection
* ⚙️ Manual path configuration when automatic detection doesn't work
* 🧩 Parses Space Engineers `.sbc` blueprint files directly
* 💻 Completely command-line based
* 📦 Minimal dependencies
* 🔒 No external services or APIs required

---

## Requirements

The script is written in Bash and intentionally keeps its dependencies to a minimum.

### Required

* Linux
* Bash
* `xmllint`

`xmllint` is used to parse the XML contained within Space Engineers `.sbc` blueprint files.

`xmllint` is already included with many Linux distributions. If it isn't installed on your system, it is normally provided by the `libxml2` utilities package.

On Debian/Ubuntu/Kubuntu:

```bash
sudo apt install libxml2-utils
```

That's it.

---

## Installation

There is no installer required.

Simply download the **two files** from this repository and place them in the same directory.

Once downloaded, make the script executable:

```bash
chmod +x se-calc
```

You can then run it directly:

```bash
./se-calc
```

Or provide a blueprint name:

```bash
./se-calc MyBlueprint
```

### Using Git

If you prefer to clone the repository:

```bash
git clone https://github.com/odium/se-calc.git
cd se-calc
chmod +x se-calc
```

Then:

```bash
./se-calc
```

---

## Steam & Blueprint Detection

The script **should automatically locate your Steam Library** and, from there, find your local Space Engineers Blueprint collection.

This is designed to work without requiring you to hard-code your Steam installation path.

However, every Linux system is different in its own special way.

Steam can be installed in different locations, libraries can exist on separate drives, and Space Engineers itself may be installed somewhere other than the default Steam library.

If automatic detection is unable to locate your library or blueprint collection, you can simply define the paths manually.

---

## Configuration

Configuration options are located at the **top of the script**.

If automatic Steam Library detection doesn't work on your system, edit the relevant path variables and point them at your Steam Library and/or Blueprint collection.

This is intentionally kept simple — there is no separate configuration file to maintain.

---

## Usage

Run the calculator with the name of the blueprint:

```bash
./se-calc MyBlueprint
```

The calculator will locate the corresponding blueprint in your local collection and display the required components.

For example:

```text
 SE BLUEPRINT CALCULATOR
 ▶ Blueprint: DaBorg 

          Component Requirements
────────────────────────────────────────────
  Component                   Required
────────────────────────────────────────────
 • SteelPlate                  10154
────────────────────────────────────────────
 • Construction                 3265
────────────────────────────────────────────
 • Superconductor               2040
────────────────────────────────────────────
```

The exact output will, of course, depend on the blueprint being calculated.

---

## PCU Calculation

Space Engineers' **PCU (Performance Cost Units)** system provides a measure of the performance impact of blocks within a build.

While building a ship or structure, knowing the component requirements is useful — but knowing the total PCU cost can be just as important, particularly when working within PCU limits.

SE Calculator therefore includes PCU calculation alongside the component breakdown.

For example:

```text
SE BLUEPRINT CALCULATOR
 ▶ Blueprint: DaBorg 
 ▶ Total Blueprint PCU: 3595 

                       PCU Expenses
─────────────────────────────────────────────────────────────
Component                                     PCU      Per
─────────────────────────────────────────────────────────────
LargeGatlingTurret                            450      225
─────────────────────────────────────────────────────────────
LargeGatlingTurretReskin                      450      225
─────────────────────────────────────────────────────────────
InsetConnector                                375      125
─────────────────────────────────────────────────────────────
SlideDoor                                     230      115
─────────────────────────────────────────────────────────────
```

---

## How It Works

Space Engineers blueprints are stored as `.sbc` files containing XML data.

Rather than relying on a dedicated Space Engineers library or external application, this project uses `xmllint` to extract the relevant information directly from those files.

Custom parser functions are used to locate and process the required data.

This was an intentional design choice.

The goal was to keep the script:

* **Self-contained**
* **Lightweight**
* **Portable**
* **Easy to understand**
* **Free from unnecessary dependencies**

There is no database to maintain and no external service involved.

The calculator simply reads the blueprint data that already exists on your machine.

---

## Why Bash?

Could this have been written in Python?

Absolutely.

Would Python have made some parts of this considerably easier?

Probably.

But this is a **Linux command-line utility**, and Bash is already available on virtually every Linux system.

Keeping the project in Bash also means there is no need to install a runtime, create a virtual environment, install packages, or maintain a collection of Python dependencies just to calculate a blueprint.

Where possible, the script uses tools already common to a Linux environment.

---

## Limitations

This project is primarily intended for **Linux users running Space Engineers through Steam**.

Automatic library detection may not work with every possible Steam installation layout.

If your Steam Library is in an unusual location, the manual configuration options at the top of the script can be used instead.

Blueprint compatibility may also depend on the structure of the `.sbc` files produced by Space Engineers. Changes to the game's blueprint format could therefore require updates to the parser.

---

## Contributing

Bug reports, improvements and pull requests are welcome.

If you encounter a blueprint that produces incorrect results, please include:

* The blueprint name
* The Space Engineers version
* Your Linux distribution
* The relevant calculator output
* Any useful error messages

If possible, a copy of the affected `.sbc` file is also extremely helpful.

---

## License

See the `LICENSE` file included with this repository.

---

## Disclaimer

This is an independent community project and is **not affiliated with or endorsed by Keen Software House** or Space Engineers.

**Space Engineers** is a trademark of Keen Software House.
