---
name: vulkan
description: Answer questions about Vulkan and MoltenVK by referencing local cloned repos. Use this skill whenever the user asks anything about Vulkan, MoltenVK, graphics programming, GPU APIs, render passes, pipelines, synchronization, extensions, validation layers, or Metal interop. Always consult the local repos before answering — do not rely solely on training knowledge.
---

# Vulkan & MoltenVK Local Reference Skill

When answering any question about Vulkan or MoltenVK, always consult the local repos first. They are located inside this skill's `references/` folder:

```
references/Vulkan-Docs/       ← Official Vulkan spec and reference pages
references/Vulkan-Headers/    ← vulkan.h, vk_platform.h, extension headers
references/Vulkan-Guide/      ← Best practices and conceptual guides
references/MoltenVK/          ← MoltenVK source and Metal interop
references/Vulkan-ValidationLayers/  ← Validation layer source, VUID checks, and docs
```

## How to use the repos

### Answering API questions
1. Check `references/Vulkan-Headers/include/vulkan/` for the actual struct/enum/function signatures
2. Check `references/Vulkan-Docs/chapters/` for spec language and usage rules
3. Cross-reference `references/Vulkan-Guide/` for best practice guidance

### Answering MoltenVK questions
1. Check `references/MoltenVK/MoltenVK/` for the Metal translation layer source
2. Check `references/MoltenVK/Docs/` for MoltenVK-specific docs and known limitations
3. Note any Metal/MoltenVK gaps or workarounds that differ from standard Vulkan behavior

### Answering validation / VUID questions
1. Search `references/Vulkan-ValidationLayers/layers/` for the check implementation
2. Check `references/Vulkan-ValidationLayers/docs/` for feature docs (best_practices, core_checks, debug_printf, gpu_av, synchronization, etc.)
3. Use these to explain what a validation error means, which VUID it maps to, and how the layer enforces it

### Answering conceptual questions
- Prefer `Vulkan-Guide` for high-level concepts (render passes, synchronization, memory management)
- Prefer `Vulkan-Docs` for precise spec-level answers
- Always note if MoltenVK has known differences from the Vulkan spec

## Key locations to know

| Repo | Key paths |
|------|-----------|
| Vulkan-Headers | `references/Vulkan-Headers/include/vulkan/vulkan_core.h` |
| Vulkan-Docs | `references/Vulkan-Docs/chapters/`, `appendices/`, `xml/vk.xml` |
| Vulkan-Guide | `references/Vulkan-Guide/chapters/`, `chapters/extensions/` |
| MoltenVK | `references/MoltenVK/MoltenVK/`, `Docs/MoltenVK_Runtime_UserGuide.md` |
| Vulkan-ValidationLayers | `references/Vulkan-ValidationLayers/layers/`, `docs/` |

## Answering strategy

- **Always grep or read local files** before answering — training data may be outdated on extension support or spec revisions
- When a struct or function is asked about, find its definition in `vulkan_core.h` and read relevant spec sections
- If MoltenVK is involved, check whether the feature is supported on Metal and note any caveats
- Cite which repo/file your answer comes from so the user can follow up
