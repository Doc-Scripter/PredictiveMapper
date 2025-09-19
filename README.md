# PredictiveMapper

## Overview

**PredictiveMapper** is an AI-powered predictive spatial modeler that builds a conceptual map of an environment using minimal data. Unlike traditional SLAM systems that rely on continuous sensor input and heavy computation, PredictiveMapper uses a *prediction-first* approach:

* It predicts the environment layout from external geospatial or building data.
* A single camera verifies and updates these predictions.
* The result is a lightweight, scalable system for navigation.

This approach is designed for low-resource devices (e.g., Raspberry Pi + camera) and can be extended to robots and drones in future phases.

---

## Core Features

* **Predictive Spatial Reasoning**: Probabilistic, graph-based model that generates a conceptual layout (rooms, connections, dimensions) from geospatial/building data.
* **Efficient Localization**: Matches architectural features in a camera image with the predictive model instead of mapping from scratch.
* **Procedural Sketching**: Outputs a simple 2D sketch (non-photorealistic) of predicted and updated layouts.
* **Low-Resource Operation**: Optimized for CPU-bound devices; no GPU required.

---

## Roadmap

### Phase 1 – Core Model (Software-Only)

* Input: address/coordinates → fetch building footprint from OSM.
* Predict floorplan/layout using ML (CubiCasa5K, RPLAN datasets).
* Verify prediction with a single photo (door, hallway).
* Output: 2D sketch of prediction and updates.

**Tech stack**: Python, PyTorch/TensorFlow Lite, OpenCV, NetworkX, Matplotlib.

---

### Phase 2 – Urban/Building Navigation

* Use stored geodata (OSM, Microsoft Open Buildings).
* Predict and verify building/city block layouts.
* Deploy on Raspberry Pi + camera.
* Navigation in structured environments (buildings, streets).

**Tech stack additions**: Gazebo/Unity simulation, Arduino for motor control (optional).

---

### Phase 3 – Natural Environments (Jungle, Rural, Wilderness)

* Offline: use stored satellite/DEM/vegetation geodata.
* Online: classify terrain type from camera (forest, clearing, river).
* Predict “escape maps” with safe paths.
* Continuous verification + updates during navigation.

**Datasets**: Sentinel-2, Copernicus DEM, Mapillary ground photos.

---

## Use Cases

* **Robotics**: Lightweight mapping for indoor robots or drones.
* **Emergency Response**: Rapid map generation in unknown buildings.
* **AR Systems**: Efficient map prediction for AR glasses without full 3D SLAM.
* **Outdoor Navigation**: Future use in unstructured environments.

---

## Installation (Phase 1 – Prototype)

```bash
# clone the repo
git clone https://github.com/yourusername/PredictiveMapper.git
cd PredictiveMapper

# create environment
python3 -m venv venv
source venv/bin/activate

# install dependencies
pip install -r requirements.txt
```

---

## Usage (Phase 1 – Prototype)

1. **Predict Floorplan**

   ```bash
   python predict.py --address "Some Building Address"
   ```

   Outputs a predicted floorplan sketch.

2. **Verify with Photo**

   ```bash
   python verify.py --image front_door.jpg
   ```

   Updates the prediction with camera input.

3. **Visualize**

   ```bash
   python visualize.py
   ```

   Displays the 2D sketch of current map.

---

## Future Plans

* Integrate real-time camera localization.
* Deploy on Raspberry Pi + PiCam.
* Add navigation modules (A\* pathfinding, obstacle avoidance).
* Expand datasets for natural environment mapping.

---

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## License

This project is licensed under the MIT License.
