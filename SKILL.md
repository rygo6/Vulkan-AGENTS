---
name: vulkan
description: Use local specifications, headers, validation layers, and implementation source to answer questions and develop or debug Vulkan and MoltenVK code. Use for Vulkan API behavior, synchronization, extensions, validation errors, and Vulkan-to-Metal translation.
---

# Vulkan & MoltenVK Local Reference Skill

Search the relevant local sources before answering technical questions. Paths below are relative to this skill directory; read only the sources needed for the request.

```text
references/Vulkan-Docs/             ← Official Vulkan spec and reference pages
references/Vulkan-Headers/          ← vulkan.h, vk_platform.h, extension headers
references/Vulkan-Guide/            ← Best practices and conceptual guides
references/MoltenVK/                ← MoltenVK source and Metal interop
references/Vulkan-ValidationLayers/ ← Validation layer source, VUID checks, and docs
references/Vulkan-Samples/          ← Khronos implementation examples
```

Identify the target Vulkan version, enabled extensions and features, and driver when they affect the answer. Use `metal` for direct Metal API work.

## How to use the repos

### Answering API questions

1. Check `references/Vulkan-Headers/include/vulkan/` for the actual struct/enum/function signatures.
2. Check `references/Vulkan-Docs/chapters/` for spec language and usage rules.
3. Cross-reference `references/Vulkan-Guide/` for best practice guidance.

### Answering MoltenVK questions

1. Check `references/MoltenVK/MoltenVK/` for the Metal translation layer source.
2. Check `references/MoltenVK/Docs/` for MoltenVK-specific docs and known limitations.
3. Note any Metal/MoltenVK gaps or workarounds that differ from standard Vulkan behavior.

### Answering validation / VUID questions

1. Search `references/Vulkan-ValidationLayers/layers/` for the check implementation.
2. Check `references/Vulkan-ValidationLayers/docs/` for feature docs (best_practices, core_checks, debug_printf, gpu_av, synchronization, etc.).
3. Match the VUID to the relevant valid-usage requirement in `references/Vulkan-Docs/`. Use the layer source to explain enforcement; distinguish specification requirements from best-practice warnings.

### Answering conceptual questions

- Prefer `Vulkan-Guide` for high-level concepts (render passes, synchronization, memory management).
- Prefer `Vulkan-Docs` for precise spec-level answers.
- Use `references/Vulkan-Samples/` for implementation examples; verify the behavior they illustrate against the specification.

## Key locations to know

| Repo | Key paths |
|------|-----------|
| Vulkan-Headers | `references/Vulkan-Headers/include/vulkan/vulkan_core.h` |
| Vulkan-Docs | `references/Vulkan-Docs/chapters/`, `appendices/`, `xml/vk.xml` |
| Vulkan-Guide | `references/Vulkan-Guide/chapters/`, `chapters/extensions/` |
| MoltenVK | `references/MoltenVK/MoltenVK/`, `Docs/MoltenVK_Runtime_UserGuide.md` |
| Vulkan-ValidationLayers | `references/Vulkan-ValidationLayers/layers/`, `docs/` |

## Answering strategy

- For structs and functions, find the declaration in the relevant header under `include/vulkan/` and read the matching specification sections.
- If MoltenVK is involved, verify support in the target MoltenVK version and device; Metal support alone does not establish MoltenVK support.
- Cite the source files and relevant sections used. Make local file links resolvable from the user's workspace.

## Reference availability and versions

- Local checkouts are snapshots. Match the sources to the user's target version; verify current claims against official upstream sources when freshness matters. Do not silently update existing checkouts.
- If a needed submodule is missing, initialize only that reference with `git submodule update --init -- references/<repo>` from this skill directory. Omit `--recursive`; nested build dependencies are unnecessary for source lookup.
- If a source remains unavailable, state the limitation and use an official upstream source when accessible. Do not present an unverified recollection as a source-backed conclusion.
