# Carvetto

**CNC design and toolpath software for woodworkers, hobbyists and small shops.**

Carvetto is a CAD/CAM program for 2D and 2.5D machining and 3D relief carving. You draw (or import) your design, tell it which tool and machine you are using, generate toolpaths, watch a simulation of the cut, and save G-code for your controller. It runs on Windows and Linux.

<!-- TODO: screenshots -->

This page is where you download Carvetto. Each release lists its installers under **Releases** on the right-hand side of this page.

## What you can do with it

**Draw and edit**
- Draw rectangles, circles, ellipses, polygons, stars and arcs, and edit vectors node by node.
- Move, scale, rotate and mirror, align and distribute, and make array, circular and along-a-path copies.
- Join, close, weld, subtract, trim, extend, fillet (including dog-bone and T-bone corners), offset, and build boundaries.
- Check a drawing for problems before cutting: open, duplicate, tiny, self-intersecting and wrong-direction vectors.
- Snap to geometry and a grid, add dimensions (linear, aligned, angular, radial) and use document variables in numeric fields.
- Add text, text in a box, or text on a curve, and convert it to curves. A serif font is built in.
- Trace a bitmap into vectors.
- Organise a job with layers and multiple sheets, with undo and redo history.
- Keep a clipart library from folders on your computer.

**Jobs and units**
- Single-sided, double-sided (flip) and rotary jobs.
- Work in millimetres or inches.
- Set up your tools, machines and materials in a tool database. A starter set is included.

**Toolpaths**
- Profile (with tabs, lead moves and cutter compensation), pocket, drill, drill bank, engrave, V-carve, chamfer, fluting, prism, thread milling and rounding.
- Inlays: straight inlay and V-carve inlay (plug and pocket).
- Image engrave, which turns a picture into a depth-varying engraving.
- Keep-out zones, toolpath tiling for work larger than your machine, and a job sheet (a printable summary with PDF output).
- Laser toolpaths: cut/fill, picture and sketch engraving.

**3D relief carving**
- Build relief models from components arranged in levels.
- Create shapes from vectors (flat, round, angled, smooth, custom), from a bitmap, or from an imported 3D model.
- Two-rail sweep, extrude and weave, turn and spin, textured areas, smoothing, embossing, slicing and draft.
- Sculpt with brushes.
- Import STL and OBJ models. Export STL, OBJ and greyscale heightmaps.
- 3D rough and finish toolpaths (including rest machining), moulding, and projecting 2D toolpaths onto a model.

**Rotary work**
- Rotary job setup, an auto-wrapping view, wrapped fluting and spiral layouts, and post-processor support for wrapping.

**Preview and output**
- Material-removal simulation with machining-time estimates.
- G-code comes from plain-text post-processor templates (the `.pp` format). Included posts:
  Grbl (mm and inch), Grbl laser mode, Mach3 (mm and inch), Mach4, LinuxCNC (mm and inch) and Marlin.
- You can edit posts or add your own.

**Files and scripting**
- Native `.carv` project files, which store your toolpaths with the design.
- Import and export DXF drawings. Import bitmaps and 3D models (see above).
- Import cabinet-style parts lists through a mapping file.
- Lua scripting for add-ons ("gadgets"), run in a sandbox. Included gadgets: Celtic weave, drag knife, keyhole, job-sheet editor and DXF batch.

## A typical workflow

1. **New Job.** Choose single-sided, double-sided or rotary, set the material size and thickness, and pick millimetres or inches.
2. **Bring in your design.** Import a DXF, or draw shapes and add text in Carvetto.
3. **Tidy up.** Join open shapes, offset, trim and run the vector check.
4. **Set up your tools.** Open *Setup > Tools, Machines and Materials* and pick or add the end mill, V-bit or drill and your machine.
5. **Add toolpaths.** For example a pocket, then a profile with tabs to cut the part out, or a V-carve for lettering. Each toolpath has a form with depth, passes and so on, and recalculates when you change it.
6. **Preview.** Run the simulation to see the cut and the estimated time. Adjust and recalculate.
7. **Save toolpaths.** Pick the post-processor for your controller and save the G-code file.
8. **Cut.** Load the file in your machine's sender or controller software.

For relief carving, build the model in the Model panel (components, levels, shapes, sweeps, sculpting), then add 3D rough and finish toolpaths and preview them in the 3D view.

## Download and install

Get the files for the latest version from the **Releases** page of this repository. Every release includes a `SHA256SUMS` file for checking your download.

### Windows

1. Download `Carvetto-<version>-win64.exe`.
2. Run it and follow the installer.
3. Start Carvetto from the Start menu. Double-clicking a `.carv` file opens it.

### Linux

Pick whichever package suits your system.

- **Debian / Ubuntu (DEB):** `sudo apt install ./carvetto_<version>_amd64.deb`
- **Fedora / openSUSE (RPM):** `sudo dnf install ./carvetto-<version>-1.x86_64.rpm`
- **AppImage (any recent distribution):**
  ```sh
  chmod +x Carvetto-<version>-x86_64.AppImage
  ./Carvetto-<version>-x86_64.AppImage
  ```

The exact file names are shown on each release.

### Check your download

Put `SHA256SUMS` in the same folder as the files you downloaded.

- **Linux:** `sha256sum -c SHA256SUMS --ignore-missing`
- **Windows (PowerShell):** `Get-FileHash .\Carvetto-<version>-win64.exe -Algorithm SHA256`, then compare the result with the matching line in `SHA256SUMS`.

If the hashes do not match, download the file again.

## System requirements

- 64-bit Windows 10 or 11, or a 64-bit Linux distribution of roughly Ubuntu 24.04's age or newer (the Linux packages are built on Ubuntu 24.04).
- A screen and graphics driver that run standard desktop applications. The 3D view is part of the program, so no separate software is needed.
- Carvetto produces G-code files. To cut, you need a CNC machine and controller or sender software of your own.

<!-- TODO: confirm minimum RAM / disk / GPU figures after testing on low-end machines -->

## Reporting a problem

Please open an issue in the **Issues** tab of this repository. Include:

- the Carvetto version (shown in *Help > About*) and your operating system,
- what you did and what you expected,
- a small `.carv` file that shows the problem, if you can share one.

## Roadmap

Not in Carvetto yet, but planned: drawing and editing vectors directly in the 3D view, plate production from spreadsheet data, printing, translations into other languages, built-in user documentation, autosave and crash recovery, and a more general part-nesting tool.
