# Vulkan-AGENTS

An agent skill that answers Vulkan and MoltenVK questions by referencing locally cloned official repositories, rather than relying solely on training data. It is agent-agnostic and works with any coding agent that supports skills (Claude Code, Codex, etc.).

### Reference repos included

| Repo | Purpose |
|------|---------|
| `references/Vulkan-Docs` | Official Vulkan spec and reference pages |
| `references/Vulkan-Headers` | `vulkan.h`, `vk_platform.h`, extension headers |
| `references/Vulkan-Guide` | Best practices and conceptual guides |
| `references/MoltenVK` | MoltenVK source and Metal interop |
| `references/Vulkan-Samples` | Khronos examples for rendering patterns, pipelines, and extensions |
| `references/Vulkan-ValidationLayers` | Validation checks, VUID enforcement, and layer documentation |

## Installation

Install once into the shared agent skills directory, then symlink it into each agent's skills folder.

The reference repositories are Git submodules. Initialize them without nested dependencies for
source lookup:

```bash
git clone git@github.com:rygo6/Vulkan-AGENTS.git ~/.agents/skills/vulkan
cd ~/.agents/skills/vulkan
git submodule update --init
```

Do not pass `--recursive` or clone with `--recurse-submodules` for source lookup. Vulkan-Samples
has nested build dependencies and assets that are unnecessary for reading its implementation.

The commands above use the recorded reference revisions. To deliberately refresh existing
references, review local changes first, then run `git submodule update --remote` and inspect the result.

Then link it into the agents you use:

```bash
mkdir -p ~/.claude/skills ~/.codex/skills
ln -s ~/.agents/skills/vulkan ~/.claude/skills/vulkan
ln -s ~/.agents/skills/vulkan ~/.codex/skills/vulkan
```

On Windows, use `mklink /J` to create a junction instead (run in `cmd`, no admin rights needed):

```bat
mklink /J "%USERPROFILE%\.claude\skills\vulkan" "%USERPROFILE%\.agents\skills\vulkan"
mklink /J "%USERPROFILE%\.codex\skills\vulkan"  "%USERPROFILE%\.agents\skills\vulkan"
```

## Usage

Once installed, request the `vulkan` skill by name or use your agent’s skill picker or invocation syntax.
