# Trace: AI hardware design, built on KiCad

**Trace is an AI hardware design tool.** Describe the device you want in plain words, and Trace designs the circuit board (schematic, parts, layout and wiring) and a 3D-printable case for it, checks the design, and helps you order the board. This repository is the source code of the Trace app, a modified version of the KiCad EDA software.

- **Get the Trace app** (macOS, Windows, Linux): [buildwithtrace.com/download](https://buildwithtrace.com/download)
- **New to electronics?** [How to design hardware with AI](https://buildwithtrace.com/design-hardware-with-ai) and [Design your first hardware](https://docs.buildwithtrace.com/guides/first-hardware/)
- **Using Altium Designer, KiCad or Autodesk Fusion?** The [Trace Plugin](https://buildwithtrace.com/plugin) brings Trace's assistant into your design tool.
- **Docs:** [docs.buildwithtrace.com](https://docs.buildwithtrace.com)

> **Important:** Trace is based on [KiCad](https://www.kicad.org/), an open-source electronics design automation suite. This is an independent fork created and maintained by the Trace team. Trace is not affiliated with, endorsed by, or supported by the KiCad project or The Linux Foundation.

For how to use Trace, see the [Trace documentation](https://docs.buildwithtrace.com). For contributing, see the [contribution guide](https://docs.buildwithtrace.com/contributing/overview/) and [CONTRIBUTING.md](CONTRIBUTING.md).

---

## About Trace

Trace extends KiCad's schematic and PCB editors with an AI assistant that designs with you:
- **Describe it, Trace builds it**: in Flow, describe a board in plain words and Trace picks real parts, draws the schematic, lays out and routes the board and checks its own work.
- **Parts**: Trace's component catalog, and new symbols, footprints and 3D models built from a datasheet.
- **Placement and routing**: free basic routing and an advanced placement and routing engine.
- **Checks and simulation**: ERC and DRC, including manufacturers' rule sets, and circuit simulation explained in plain words.
- **Enclosures**: Trace Mechanical designs a 3D-printable case around the board (STL, 3MF, STEP).
- **Manufacturing**: Gerber, drill, BOM and placement files, or send the board to PCBWay or Pikkolo Assembly from inside the app.
- **Teams**: Team Workspaces with cloud projects, branches and pull requests.

The assistant and its services are proprietary and need a Trace account; see [Proprietary Components](#proprietary-components) and [pricing](https://buildwithtrace.com/pricing).

## License & Compliance

### Open Source License

Trace is released under the **GNU General Public License v3** (GPLv3), the same license as KiCad.

- **License Text**: See [LICENSE](LICENSE) file in this repository
- **Source Code**: This repository contains the complete source code for Trace
- **Full Source Archive**: Available at https://github.com/buildwithtrace/trace-public

As required by GPLv3, you are free to:
- Use Trace for any purpose
- Study and modify the source code
- Share copies with others
- Distribute modified versions (under GPLv3)

### Copyright & Attribution

```
Copyright (C) 2025-2026 Trace Developers (see TRACE_AUTHORS.txt)
Copyright (C) 1992-2024 KiCad Developers (see AUTHORS.txt)

Trace incorporates substantial code from the KiCad project.
KiCad is copyright its contributors and licensed under GPLv3.
```

**Modification Notice**: This software is a modified version of KiCad EDA, adapted by the Trace team starting December 2025. Original KiCad code and modifications are both licensed under GPLv3.

### Trademark Notice

**KiCad** is a registered trademark of The Linux Foundation. All rights reserved.  
**Trace** is a trademark of the Trace team.

Trace is an independent product and is not affiliated with or endorsed by the KiCad project, The Linux Foundation, or any KiCad contributors. Any bugs, issues, or support requests for Trace should be directed to the Trace team, not the KiCad project.

### Third-Party Licenses

This software includes components under various open-source licenses:
- **KiCad Libraries**: Creative Commons Attribution-ShareAlike 4.0 (CC-BY-SA 4.0)
- **Various Components**: MIT, BSD, Apache, and other permissive licenses
- See individual `LICENSE*` files in subdirectories for details

### Proprietary Components

> **Important:** The [`trace/`](trace/) directory contains Trace's proprietary AI-native design modules and is **NOT** covered by GPLv3. All files under `trace/` and its subdirectories are **All Rights Reserved** and are provided for reference only. See [`trace/LICENSE`](trace/LICENSE) for the full terms. Contact hello@buildwithtrace.com for licensing inquiries.

### No Warranty

```
THIS SOFTWARE IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

See the [LICENSE](LICENSE) file for complete GPL warranty disclaimer.

---

## Building Trace from Source

### Prerequisites

- **CMake** 3.16 or later
- **C++ compiler** with C++17 support (GCC 8+, Clang 8+, MSVC 2019+)
- **Python** 3.8+ with wxPython
- **Git** for cloning the repository
- Platform-specific dependencies (see below)

### Build Instructions

#### macOS

Use our official Mac builder:
```bash
git clone https://github.com/buildwithtrace/trace-mac-builder
cd trace-mac-builder
python build.py
```

See [trace-mac-builder](https://github.com/buildwithtrace/trace-mac-builder) for detailed instructions.

#### Windows

Use our official Windows builder:
```bash
git clone https://github.com/buildwithtrace/trace-win-builder
cd trace-win-builder
# Follow instructions in repository
```

See [trace-win-builder](https://github.com/buildwithtrace/trace-win-builder) for detailed instructions.

#### Linux

```bash
# Install dependencies (Ubuntu/Debian example)
sudo apt-get update
sudo apt-get install -y cmake g++ git python3 python3-wxgtk4.0 \
    libboost-all-dev libglew-dev libcairo2-dev libcurl4-openssl-dev \
    libssl-dev libngspice0-dev libocct-*-dev swig

# Clone and build
git clone https://github.com/buildwithtrace/trace-public
cd trace-public
mkdir -p build/release
cd build/release
cmake ../.. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)
sudo make install
```

For detailed build documentation, see [Developer Documentation](https://docs.buildwithtrace.com).

---

## Files

* [AUTHORS.txt](AUTHORS.txt) - KiCad authors, contributors, document writers and translators (see [original on GitLab](https://gitlab.com/kicad/code/kicad/-/blob/master/AUTHORS.txt))
* [TRACE_AUTHORS.txt](TRACE_AUTHORS.txt) - Trace-specific contributors and developers
* [CMakeLists.txt](CMakeLists.txt) - Main CMAKE build tool script
* [copyright.h](copyright.h) - A very short copy of the GNU General Public License to be included in new source files
* [Doxyfile](Doxyfile) - Doxygen config file for Trace
* [INSTALL.txt](INSTALL.txt) - The release (binary) installation instructions
* [uncrustify.cfg](uncrustify.cfg) - Uncrustify config file for uncrustify sources formatting tool
* [_clang-format](_clang-format) - clang config file for clang-format sources formatting tool

---

## Getting Started

1. **Download**: Get the Trace app from [buildwithtrace.com/download](https://buildwithtrace.com/download)
2. **Install**: Run the installer for your platform ([system requirements](https://docs.buildwithtrace.com/installation/))
3. **Sign In**: Create a Trace account. The editors and basic routing are free; the AI assistant uses a plan, credits or a 7-day trial ([billing](https://docs.buildwithtrace.com/guides/billing/))
4. **Start Designing**: Trace opens in Flow. Describe what you want to build, for example "A USB-C powered board with an ESP32, a temperature sensor and a status LED"

### What you can ask

- Describe a whole board: "A small USB-C powered board with an ESP32 and a temperature sensor"
- Ask questions: "How do I add decoupling capacitors?"
- Get component suggestions: "Find a low-power MCU for battery operation"
- Ask for a case: "Design a 3D-printed case for this board with a snap-on lid"

---

## Documentation

- **Beginner's guide**: [Design your first hardware](https://docs.buildwithtrace.com/guides/first-hardware/)
- **User Guide**: [Your first PCB](https://docs.buildwithtrace.com/guides/first-pcb/)
- **Partner API**: [docs.buildwithtrace.com/api/partner-overview](https://docs.buildwithtrace.com/api/partner-overview/)
- **Discord Community**: [Join us on Discord](https://discord.gg/UNUvQxneCr) - Get help, report bugs, discuss features, and stay updated
- **KiCad Documentation**: For core EDA features, [KiCad docs](https://docs.kicad.org/) may be helpful

---

## Project Structure

- **[3d-viewer](3d-viewer)** - Sourcecode of the 3D viewer
- **[bitmap2component](bitmap2component)** - Sourcecode of the bitmap to PCB artwork converter
- **[cmake](cmake)** - Modules for the CMAKE build tool
- **[common](common)** - Sourcecode of the common library
- **[cvpcb](cvpcb)** - Sourcecode of the CvPCB tool
- **[demos](demos)** - Some demo examples
- **[doxygen](doxygen)** - Configuration for generating pretty doxygen manual of the codebase
- **[eeschema](eeschema)** - Sourcecode of the schematic editor with AI integration
- **[gerbview](gerbview)** - Sourcecode of the gerber viewer
- **[include](include)** - Interfaces to the common library
- **[kicad](kicad)** - Sourcecode of the project manager
- **[libs](libs)** - Sourcecode of Trace utilities (geometry and others)
- **[pagelayout_editor](pagelayout_editor)** - Sourcecode of the pagelayout editor
- **[patches](patches)** - Collection of patches for external dependencies
- **[pcbnew](pcbnew)** - Sourcecode of the printed circuit board editor
- **[plugins](plugins)** - Sourcecode for the 3D viewer plugins
- **[qa](qa)** - Unit testing framework for Trace
- **[resources](resources)** - Packaging resources such as bitmaps and operating system specific files
  - [bitmaps_png](resources/bitmaps_png) - Menu and program icons
  - [project_template](resources/project_template) - Project template
- **[scripting](scripting)** - Python integration for Trace
- **[thirdparty](thirdparty)** - Sourcecode of external libraries used in Trace but not written by the Trace team
- **[tools](tools)** - Helpers for developing, testing and building
- **[trace](trace)** - Trace-specific AI and integration code
- **[trace_assets](trace_assets)** - Trace branding and UI assets
- **[translation](translation)** - Translation data files
- **[utils](utils)** - Small utils for Trace, e.g. IDF, STEP, and OGL tools and converters

---

## Contributing

We welcome contributions! Trace is a fork of KiCad, and we maintain compatibility with KiCad file formats and architectural decisions. Developers familiar with KiCad will find the codebase familiar.

**Getting Started:**
- Join our [Discord community](https://discord.gg/UNUvQxneCr) - Primary hub for discussions, bug reports, questions, and announcements
- Check the [issue tracker](https://github.com/buildwithtrace/trace-public/issues) for "good first issue" labels
- For larger changes, discuss on Discord before starting work

**Important Notes:**
- All contributions must be compatible with GNU GPLv3
- By contributing, you agree to license your code under GPLv3
- Consider upstreaming useful improvements to [KiCad](https://gitlab.com/kicad/code/kicad) when applicable

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on code style, pull requests, testing, and more.

---

## Support

- **Discord**: [Join our community](https://discord.gg/UNUvQxneCr) - Get help, report bugs, discuss features, ask questions
- **Website**: [buildwithtrace.com](https://buildwithtrace.com)
- **Email**: hello@buildwithtrace.com
- **Issues**: [GitHub Issues](https://github.com/buildwithtrace/trace-public/issues)

**Note**: For issues with core KiCad functionality (not Trace-specific features), consider also reporting to the [KiCad project](https://gitlab.com/kicad/code/kicad/-/issues) to benefit the wider community.

---

## Acknowledgments

Trace is built on the excellent work of the KiCad project and its contributors. We are grateful to the KiCad developers and the broader open-source EDA community for creating a solid foundation.

**KiCad Contributors**: See [AUTHORS.txt](AUTHORS.txt) for the full list of KiCad contributors whose work is included in Trace. The original list is maintained at [gitlab.com/kicad/code/kicad](https://gitlab.com/kicad/code/kicad/-/blob/master/AUTHORS.txt).

**Trace Contributors**: See [TRACE_AUTHORS.txt](TRACE_AUTHORS.txt) for Trace-specific contributors. Copyright (C) 2025-2026 Trace Developers.

---

## Repository Information

- **Main Repository**: https://github.com/buildwithtrace/trace-public
- **Mac Builder**: https://github.com/buildwithtrace/trace-mac-builder
- **Windows Builder**: https://github.com/buildwithtrace/trace-win-builder
- **Backend API**: (Proprietary - not included in this repository)

---

**Version**: see [Releases](https://github.com/buildwithtrace/trace-public/releases)  
**Based on**: KiCad EDA  
**Modified**: since December 2025  
**License**: GNU GPLv3
