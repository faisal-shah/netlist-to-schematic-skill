# netlist-to-schematic-skill

An [agent skill](https://docs.github.com/copilot/concepts/agents/about-agent-skills)
that teaches AI coding assistants how to convert **SPICE netlists** into
publication-quality **circuit schematic diagrams** using Circuitikz (LaTeX).

## What's Included

| File | Required | Purpose |
|------|----------|---------|
| `SKILL.md` | **yes** | Main skill file — loaded by the agent framework |
| `scripts/compile_tex.py` | **yes** | Compiles Circuitikz `.tex` to PNG via pdflatex + pdftoppm |
| `README.md` | no | This file (repo documentation only) |
| `AGENTS.md` | no | AI context for developing the skill itself |
| `LICENSE` | no | MIT license text |

## Installation

### GitHub Copilot / VS Code

```bash
git clone https://github.com/faisal-shah/netlist-to-schematic-skill.git

# Option 1: project-level
mkdir -p .github/skills/netlist-to-schematic/scripts
cp netlist-to-schematic-skill/SKILL.md .github/skills/netlist-to-schematic/
cp netlist-to-schematic-skill/scripts/*.py .github/skills/netlist-to-schematic/scripts/

# Option 2: user-level (all projects)
mkdir -p ~/.copilot/skills/netlist-to-schematic/scripts
cp netlist-to-schematic-skill/SKILL.md ~/.copilot/skills/netlist-to-schematic/
cp netlist-to-schematic-skill/scripts/*.py ~/.copilot/skills/netlist-to-schematic/scripts/
```

### Claude Code

```bash
mkdir -p ~/.claude/skills/netlist-to-schematic/scripts
cp netlist-to-schematic-skill/SKILL.md ~/.claude/skills/netlist-to-schematic/
cp netlist-to-schematic-skill/scripts/*.py ~/.claude/skills/netlist-to-schematic/scripts/
```

### OpenAI Codex

```bash
mkdir -p ~/.codex/skills/netlist-to-schematic/scripts
cp netlist-to-schematic-skill/SKILL.md ~/.codex/skills/netlist-to-schematic/
cp netlist-to-schematic-skill/scripts/*.py ~/.codex/skills/netlist-to-schematic/scripts/
```

## Prerequisites

- **pdflatex** with `circuitikz` package (TeX Live or similar)
- **pdftoppm** (from `poppler-utils`) for PDF→PNG conversion
- **Python 3.10+** and **uv** for running the compile script

## Quick Start

```bash
# Compile a Circuitikz schematic to PNG
uv run scripts/compile_tex.py my_schematic.tex              # → my_schematic.png
uv run scripts/compile_tex.py my_schematic.tex --dpi 600    # higher resolution
uv run scripts/compile_tex.py my_schematic.tex -o output.png # custom output path
```

## What the Skill Covers

1. **Workflow** — the 6-step netlist→schematic conversion process
2. **Netlist parsing** — how to extract topology, stages, and signal paths
3. **Layout strategy** — left-to-right flow, ground bus, coordinate spacing, stage grouping
4. **Circuitikz template** — base LaTeX with recommended settings
5. **Component mapping** — complete SPICE→Circuitikz translation table
6. **Complex patterns** — transformer (core lines, dots), switches, parallel branches
7. **Label placement** — systematic rules to prevent the #1 quality problem (overlap)
8. **Worked example** — complete forward converter schematic demonstrating all techniques
9. **Compile→view→iterate** — the feedback workflow with review checklist
10. **Common pitfalls** — table of frequent errors and their fixes

## Related Skills

For circuit **simulation** (running ngspice, parsing rawfiles, plotting
waveforms), see
[circuit-sim-skill](https://github.com/faisal-shah/circuit-sim-skill).

## Compatible Agents

- GitHub Copilot (CLI, VS Code, JetBrains)
- Claude Code / Claude.ai
- OpenAI Codex
- Any agent supporting the SKILL.md convention

## License

MIT
