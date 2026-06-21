# Vulkan-AGENTS

An agent skill that answers Vulkan and MoltenVK questions by referencing locally cloned official repositories, rather than relying solely on training data. It is agent-agnostic and works with any coding agent that supports skills (Claude Code, Codex, etc.).

### Reference repos included

| Repo | Purpose |
|------|---------|
| `references/Vulkan-Docs` | Official Vulkan spec and reference pages |
| `references/Vulkan-Headers` | `vulkan.h`, `vk_platform.h`, extension headers |
| `references/Vulkan-Guide` | Best practices and conceptual guides |
| `references/MoltenVK` | MoltenVK source and Metal interop |
| `references/Vulkan-Samples` | Khronos canonical samples (auxiliary patterns: matrix conventions, pipeline setups, extension demos) |

## Installation

Install once into the shared agent skills directory, then symlink it into each agent's skills folder.

Clone with `--recurse-submodules` — the reference repos are git submodules:

```bash
git clone --recurse-submodules git@github.com:rygo6/Vulkan-AGENTS.git ~/.agents/skills/vulkan
cd ~/.agents/skills/vulkan
git submodule update --remote
```

Then link it into the agents you use:

```bash
mkdir -p ~/.claude/skills ~/.codex/skills
ln -s ~/.agents/skills/vulkan ~/.claude/skills/vulkan
ln -s ~/.agents/skills/vulkan ~/.codex/skills/vulkan
```

## Usage

Once installed, invoke `/vulkan` from any agent that supports skills.
