# Claude Vulkan Skill

A Claude Code skill that answers Vulkan and MoltenVK questions by referencing locally cloned official repositories, rather than relying solely on training data.

### Reference repos included

| Repo | Purpose |
|------|---------|
| `references/Vulkan-Docs` | Official Vulkan spec and reference pages |
| `references/Vulkan-Headers` | `vulkan.h`, `vk_platform.h`, extension headers |
| `references/Vulkan-Guide` | Best practices and conceptual guides |
| `references/MoltenVK` | MoltenVK source and Metal interop |
| `references/Vulkan-Samples` | Khronos canonical samples (auxiliary patterns: matrix conventions, pipeline setups, extension demos) |

## Installation

Clone with `--recurse-submodules` — the reference repos are git submodules:

```bash
git clone --recurse-submodules https://github.com/rygo6/Vulkan-AGENTS.git ~/.claude/skills/vulkan
cd ~/.claude/skills/vulkan
git submodule update --remote
```

## Usage

Once installed open Claude Code and run `/vulkan`.
