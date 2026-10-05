<div align="center">

# 🚑 City Navigation & Emergency Route Planner

### Shortest paths across a real city street network — that reroute instantly when a road is reported blocked.

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![OSMnx](https://img.shields.io/badge/OSMnx-OpenStreetMap-7EBC6F?style=flat-square&logo=openstreetmap&logoColor=white)
![NetworkX](https://img.shields.io/badge/NetworkX-graphs-2C7FB8?style=flat-square)
![GeoPandas](https://img.shields.io/badge/GeoPandas-139C5A?style=flat-square)
![Leaflet](https://img.shields.io/badge/Leaflet-map_UI-199900?style=flat-square&logo=leaflet&logoColor=white)

*CPSC 535 (Advanced Algorithms) — Group 1, Project 2 · Cal State Fullerton*

</div>

---

## ✨ Features

- 🗺️ **Real road network** — Fullerton, CA's drivable streets pulled from OpenStreetMap with OSMnx as a NetworkX graph
- 📍 **Pick start and destination** from points of interest (cafés) on an interactive Leaflet map
- 🧮 **Floyd–Warshall all-pairs shortest paths** between every café, implemented from scratch (`floyd_warshall.py`)
- 🚧 **Report a blockage** — blockages are applied to the graph and the route is recomputed around them
- ⚡ **Cached OSM responses** (`cache/`) so repeated runs don't re-download the network

## 🔌 API

| Endpoint | Method | Purpose |
|---|---|---|
| `/` | GET | Map UI |
| `/get_cafes` | GET | Points of interest for the source/destination pickers |
| `/calculate_path` | POST | Shortest path between two points, honouring blockages |
| `/report_blockage` | POST | Mark a road segment as blocked |
| `/about` | GET | Project info |

## 🚀 Run it

```bash
git clone https://github.com/SaiSatyaJagannadh/City-Navigation.git
cd "City-Navigation/CPSC535_Group1_Project2-main 2"
pip install flask osmnx networkx geopandas shapely matplotlib numpy pandas
python main.py        # → http://127.0.0.1:5000
```

## 🧠 Why Floyd–Warshall?

All-pairs shortest paths are computed once (O(V³)) so any source/destination query afterwards is a lookup — a good fit for an emergency tool where the same area is queried repeatedly. When a blockage is reported, distances are recomputed with that edge removed.

---

<div align="center">

**Built by [Sai Satya Jagannadh Doddipatla (DJ)](https://saisatyajagannadh.github.io/PersonalPortfolio/)** & team · ⭐ Star the repo if it helped

</div>
