# Condensation

A Houdini condensation-droplet toolset by **Aseda Media**.

Condensation is a set of Houdini Digital Assets (HDAs) that build, simulate, and mesh realistic condensation droplets on a collision surface.

> ℹ️ **Distributed as black-box (locked) HDAs.** The internals are not editable — drive the look through the exposed parameters.

## The toolset

| HDA | Role |
|-----|------|
| **am_Condensation_Source** | Builds the initial droplet source: a static, sim-ready point distribution on a collision surface — where droplets exist, how large they start, which points can release, and the attributes the Solver needs (pinning, delay, class). |
| **am_Condensation_Solver** | Animates the source points through release, sliding, absorption, trails, and falling. Owns motion and state. |
| **am_Condensation_Surface** | Builds the final renderable geometry from Solver points: VDB / particle-fluid meshing, contact cutting, sag, mist, and wetmap output. |
| **am_Condensation_Wetmap** | Generates a wetmap — a wetness texture from where the droplets have been — for shading and rendering. *(Optional, requires Houdini 21.0+.)* |

Pipeline: **Source → Solver → Surface**.

## Requirements

- **Recommended: Houdini 21.0** — the HDAs are authored and saved in build **21.0.671**.
- **Minimum: Houdini 19.5** for the core **Source**, **Solver**, and **Surface** HDAs.
- The optional **Wetmap** component (if included) requires **Houdini 21.0 or newer**.

## Install

1. Download the latest `.hda` files from the [**Releases**](../../releases) page.
2. Either drop them into a folder on your Houdini `HOUDINI_OTLSCAN_PATH` (e.g. your `otls/` directory), **or** in Houdini go to **Assets ▸ Install Digital Asset Library…** and pick each file.
3. The nodes appear in the **SOP** tab menu as `am_Condensation_Source`, `am_Condensation_Solver`, and `am_Condensation_Surface`.

## Feedback & feature requests

- 🐞 **Found a bug?** Open an [issue](../../issues/new/choose) with the **Bug report** template.
- 💡 **Want a feature?** Open an [issue](../../issues/new/choose) with the **Feature request** template.
- 💬 **Question or show-and-tell?** Use [Discussions](../../discussions).

When reporting, please include your **Houdini build**, the **HDA + version**, and a screenshot or short clip — it makes issues much faster to act on.

## License

Free to use in your own personal and commercial projects. **Redistribution, re-hosting, or resale of the HDAs is not permitted.** See [LICENSE](LICENSE).

© Aseda Media. All rights reserved.
