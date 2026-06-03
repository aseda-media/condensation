# Condensation

A Houdini condensation-droplet toolset by **Aseda Media**.

Condensation is a set of Houdini Digital Assets (HDAs) that build, simulate, and mesh realistic condensation droplets on a collision surface.

> ℹ️ **Distributed as black-box (locked) HDAs.** The internals are not editable — drive the look through the exposed parameters.

The repository itself contains the public documentation, license, and issue templates. The `.hda` files are distributed from GitHub **Releases** so the repository stays lightweight.

## The toolset

| HDA | Role |
|-----|------|
| **am_Condensation_Source** | Builds the initial droplet source: a static, sim-ready point distribution on a collision surface — where droplets exist, how large they start, which points can release, and the attributes the Solver needs (pinning, delay, class). |
| **am_Condensation_Solver** | Animates the source points through release, sliding, absorption, trails, and falling. Owns motion and state. |
| **am_Condensation_Surface** | Builds the final renderable geometry from Solver points: VDB / particle-fluid meshing, contact cutting, sag, mist, and wetmap output. |
| **am_Condensation_Wetmap** | Generates a wetmap — a wetness texture from where the droplets have been — for shading and rendering. *(Optional, requires Houdini 21.0+.)* |

Pipeline: **Source → Solver → Surface**.

## Requirements

- **Recommended: Houdini Indie 21.0**.
- The core **Source**, **Solver**, and **Surface** HDAs are intended for Houdini **19.5+**, but use the release notes for each version as the compatibility source of truth.
- The optional **Wetmap** component, if included, requires **Houdini 21.0 or newer**.

## Install

1. Download the latest `.hda` files from the [**Releases**](../../releases) page.
2. Either drop them into a folder on your Houdini `HOUDINI_OTLSCAN_PATH` (for example, `C:\Users\<you>\Documents\houdini21.0\Otls` on Windows), **or** in Houdini go to **Assets ▸ Install Digital Asset Library…** and pick each file.
3. In the **SOP** tab menu, the main nodes appear under **aMLib ▸ Utils**:
   - `am_Condensation_Solver`
   - `am_Condensation_Surface`
   - `am_Condensation_Wetmap`

`am_Condensation_Source` may appear under Houdini's **Digital Assets** tab-menu category.

## Setup tutorial

A simple YouTube setup tutorial is coming soon. It will cover installing the HDAs, wiring **Source → Solver → Surface**, and getting the first droplets moving.

## Example scene

An example setup scene is included in [`scene/`](scene/):

- `Setup_Scene.hiplc` — a simple Houdini Indie setup scene.
- `geo/Can.obj` — the sample collision/support model used by the scene.

## Basic workflow

1. Create or import the collision/support surface you want droplets to form on.
2. Add `am_Condensation_Source` and connect the support surface to input 1.
3. Connect Source output 1 to Solver input 1, and Source output 2 to Solver input 2.
4. Connect Solver output 1 to Surface input 1, and Solver output 2 to Surface input 2.
5. Tune Source first, then Solver motion, then Surface meshing/deformation.
6. If using `am_Condensation_Wetmap`, feed it from the Surface wetmap output.

## Documentation

The HDAs are documented directly inside Houdini. Each node includes parameter labels/tooltips and a Houdini help card, so you can inspect controls from the parameter interface or open the node help while working.

## Known issues

- `am_Condensation_Source` may appear under Houdini's **Digital Assets** tab-menu category instead of **aMLib ▸ Utils**.
- When using the preset, set **am_Condensation_Surface ▸ Particle Scale ▸ Growing Scale** to `1`.

## Feedback & feature requests

- 🐞 **Found a bug?** Open an [issue](../../issues/new/choose) with the **Bug report** template.
- 💡 **Want a feature?** Open an [issue](../../issues/new/choose) with the **Feature request** template.
- 💬 **Question or show-and-tell?** Use [Discussions](../../discussions).

When reporting, please include your **Houdini build**, the **HDA + version**, and a screenshot or short clip — it makes issues much faster to act on.

## A note from the author

We built this droplet and condensation setup from the ground up, together with AI, based on what we learned while developing our first droplet system.

It's fast, simple, and easy to use — and free for both personal and commercial projects.

If you make something with it, tag **[@aseda_media](https://instagram.com/aseda_media)** on Instagram. We'd love to see what you create.

## License

Free to use in your own personal and commercial projects. **Redistribution, re-hosting, or resale of the HDAs is not permitted.** See [LICENSE](LICENSE).

© Aseda Media. All rights reserved.
