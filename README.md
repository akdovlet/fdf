*This project has been created as part of the 42 curriculum by akdovlet.*

# FdF — Fil de Fer

## Description

FdF (from the French *Fil de Fer*, meaning "wireframe") is a 3D wireframe terrain renderer written in C. The goal is to read a heightmap file describing a grid of altitude values and render it as an interactive isometric wireframe projection in a graphical window.

Each point in the map file corresponds to a vertex whose X and Y coordinates represent its position on the grid and whose value represents its altitude (Z axis). Vertices are connected by lines to form a mesh, giving the illusion of a three-dimensional landscape.

Key technical features of this implementation:

- **Isometric projection** with configurable offsets along all three axes
- **Flat (top-down) view** toggle
- **Bresenham's line-drawing algorithm** for crisp, integer-accurate edge rendering
- **Quaternion-based rotation** for gimbal-lock-free 3D rotations
- **Color gradients** interpolated along edges based on altitude
- **Dynamic zoom** via the scroll wheel
- **Pan and reset** controls via keyboard
- **Custom map support** — any valid `.fdf` file can be passed as an argument

The program is built on top of [MiniLibX](https://github.com/42Paris/minilibx-linux), the lightweight X11 graphics library used at 42, alongside a custom `libft` and `ft_printf`.

---

## Instructions

### Dependencies

The following libraries must be present on your system:

- `gcc` or `cc`
- `make`
- X11 development headers (`libx11-dev`, `libxext-dev` on Debian/Ubuntu)
- `zlib` (`zlib1g-dev`)

Install them on Debian/Ubuntu with:

```bash
sudo apt install gcc make libx11-dev libxext-dev zlib1g-dev
```

### Compilation

Clone the repository and run:

```bash
git clone <repo-url> fdf
cd fdf
make
```

This will compile `libft`, `ft_printf`, and `mlx_linux` automatically before linking the final `fdf` binary.

Additional Makefile targets:

| Target   | Effect                                      |
|----------|---------------------------------------------|
| `make`   | Build the `fdf` executable                  |
| `make clean`  | Remove object files                    |
| `make fclean` | Remove object files and the binary     |
| `make re`     | Full recompile from scratch            |

### Execution

```bash
./fdf <map.fdf>
```

Example:

```bash
./fdf maps/mars.fdf
./fdf maps/42.fdf
```

The `.fdf` map format is a plain-text grid of space-separated integers representing altitudes. Optionally, each value may be followed by a comma and a hex color code (e.g. `0,0xFF0000`).

### Controls

| Input              | Action                                      |
|--------------------|---------------------------------------------|
| Arrow keys         | Pan the view (translate X/Y)                |
| Scroll wheel up    | Zoom in                                     |
| Scroll wheel down  | Zoom out                                    |
| `W` / `S`          | Adjust isometric X offset                  |
| `A` / `D`          | Adjust isometric Y offset                  |
| `K` / `L`          | Adjust isometric Z offset                  |
| `Left Shift`       | Increase Z scale (exaggerate altitude)      |
| `Left Ctrl`        | Decrease Z scale (flatten altitude)         |
| `R`                | Reset view to defaults                      |
| `F`                | Toggle flat (top-down) view                 |
| `Escape`           | Quit                                        |
| Window close (`X`) | Quit                                        |

---

## Resources

### Documentation & References

- [MiniLibX Linux documentation](https://harm-smits.github.io/42docs/libs/minilibx) — official guide to the graphical library used at 42
- [Bresenham's line algorithm — Wikipedia](https://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm) — the algorithm used for edge rendering
- [Isometric projection — Wikipedia](https://en.wikipedia.org/wiki/Isometric_projection) — mathematical basis for the isometric view
- [Quaternions and spatial rotation — Wikipedia](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation) — theory behind the quaternion rotation system implemented in this project
- [Scratchapixel — Rasterization](https://www.scratchapixel.com/) — general reference for software rasterization concepts
- [X11 Keysym reference](https://www.cl.cam.ac.uk/~mgk25/ucs/keysymdef.h) — keysym constants used for keyboard input handling

### Use of AI

AI was not used at any point during the research, design, or development of this project. The only use of AI in this repository is the **redaction of this README file**.
