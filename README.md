# 🎮 cub3D

> My first RayCaster — a 1337 school project inspired by Wolfenstein 3D.

---

## 📖 About

**cub3D** is a 42 project where you create a 3D maze using **raycasting** — the same technique used in the legendary game *Wolfenstein 3D*.  
Using the **MiniLibX** library, you render a first-person view of a map in real time, with textured walls, floor, and ceiling colors.

---

## ⚙️ Compilation

```bash
make        # Compile → cub3D
make clean  # Remove object files
make fclean # Remove object files + binary
make re     # fclean + make
```

---

## 🕹️ Run

```bash
./cub3D maps/map.cub
```

> The map must be a `.cub` file.

---

## 🗺️ Map Rules

Maps are plain text `.cub` files with two sections: **scene description** and **map grid**.

### Scene Description

| Identifier | Description | Example |
|---|---|---|
| `NO` | North wall texture path | `NO ./textures/north.xpm` |
| `SO` | South wall texture path | `SO ./textures/south.xpm` |
| `WE` | West wall texture path | `WE ./textures/west.xpm` |
| `EA` | East wall texture path | `EA ./textures/east.xpm` |
| `F` | Floor color (RGB) | `F 220,100,0` |
| `C` | Ceiling color (RGB) | `C 225,30,0` |

### Map Grid

| Character | Description |
|---|---|
| `1` | Wall |
| `0` | Empty space |
| `N` / `S` / `E` / `W` | Player start position & facing direction |

**Example `.cub` file:**
```
NO ./textures/north.xpm
SO ./textures/south.xpm
WE ./textures/west.xpm
EA ./textures/east.xpm
F 70,130,180
C 135,206,235

111111
100001
1000N1
100001
111111
```

Map rules:
- Must be **enclosed by walls** (`1`)
- Exactly **one player** spawn (`N`, `S`, `E`, or `W`)
- Only valid characters (`0`, `1`, player)

---

## 🎮 Controls

| Key | Action |
|---|---|
| `W` or `↑` | Move forward |
| `S` or `↓` | Move backward |
| `A` | Strafe left |
| `D` | Strafe right |
| `←` | Rotate camera left |
| `→` | Rotate camera right |
| `ESC` | Quit the game |

---

## ⭐ Bonus

| Feature | Description |
|---|---|
| **Mouse rotation** | Look left/right using the mouse |
| **Minimap** | Overhead 2D map displayed on screen |
| **Doors** | Openable/closable doors in the map (`2`) |
| **Animated sprites** | Weapon animations |

---

## 🔑 Key Concepts

- **Raycasting** — casting rays from the player viewpoint to calculate wall distances and heights
- **DDA algorithm** — fast grid traversal to detect wall hits
- **Texture mapping** — projecting `.xpm` textures onto walls based on hit position
- **FOV** — field of view simulation using ray angles
- **MiniLibX** — window rendering, image buffers, keyboard & mouse events
- **Map parsing** — reading and validating `.cub` files (scene info + grid)

---

## 🧪 Testing

```bash
./cub3D maps/map.cub               # Valid map
./cub3D maps/invalid.cub           # Should print error and exit
./cub3D                            # No argument → error
./cub3D maps/map.png               # Wrong extension → error
```

**Error cases handled:**
- Wrong file extension (not `.cub`)
- Invalid or missing textures
- Invalid RGB values for floor/ceiling
- Map not enclosed by walls
- Multiple or missing player spawn
- Invalid characters in map

---

## 📋 Norme

This project follows the **42 Norm**:
- Max 25 lines per function
- Max 5 functions per file
- No `for`, `do...while`, `switch`
- No more than 5 variables per function

---

## 👤 Author

ataoufik@student.1337.ma

---

*1337 School (42 NETWORK) — cub3D project*
