Here is an updated `README.md` file **without emojis**, formatted in Markdown, ready to paste into your repository. Edit the placeholders (`<your-github-username>`, `<video-link>`, etc.) to match your project.

```markdown
# testbed_navigation — ERIC Robotics Level 1 ROS2 Navigation Assignment

**Author:** Keshav Naroju  
**Date:** 2025-10-31

---

## Overview  
This repository contains my implementation for the Level 1 ROS2 Navigation assignment using the Testbed-T1.0.0 robot.  
The objective: manually launch the key components of the Nav2 stack — map loading, localization (AMCL), and autonomous navigation — using modular launch files and custom parameter configurations.

---

## Repository Structure  
```

testbed_navigation/
├── launch/
│   ├── map_loader.launch.py
│   ├── localization.launch.py
│   ├── navigation.launch.py
│   └── bringup_navigation.launch.py
└── config/
├── amcl_params.yaml
├── nav2_params.yaml
├── costmap_common_params.yaml
└── map_server_params.yaml
└── maps/
├── my_map.yaml
└── my_map.pgm
└── media/
├── navigation_demo.mp4  (or link: <video-link>)
└── map_screenshot.png
├── CMakeLists.txt
├── package.xml
└── README.md

````

---

## Build & Run Instructions  

### 1. Build the workspace  
```bash
cd ~/assignment_ws  
colcon build --symlink-install  
source install/setup.bash  
````

### 2. Launch the simulation environment

```bash
ros2 launch testbed_bringup testbed_full_bringup.launch.py
```

### 3. Load the saved map

```bash
ros2 launch testbed_navigation map_loader.launch.py
```

If the map does not appear in RViz, run:

```bash
ros2 lifecycle set /map_server configure  
ros2 lifecycle set /map_server activate  
```

### 4. Start localization (AMCL)

```bash
ros2 launch testbed_navigation localization.launch.py
```

### 5. Start navigation (Nav2 stack)

```bash
ros2 launch testbed_navigation navigation.launch.py
```

### 6. In RViz

* Set **Fixed Frame** to `map`
* Use **2D Pose Estimate** tool to provide the robot’s initial pose
* Use **2D Nav Goal** tool to send a target and observe navigation behavior

---

## Demo & Screenshots

* Demo video: `media/navigation_demo.mp4` or accessible via link: `<video-link>`
* Screenshot of map view: `media/map_screenshot.png`

---

## Key Features

* Modular launch files replacing a monolithic bringup
* Parameter configuration for AMCL, Nav2 costmaps, planners and controllers
* Use of a saved map within the Nav2 workflow
* Self-contained recorded demo of mapping, localization and navigation

---

## Known Issues & Workarounds

* RViz initially reported “No map received” because the map server lifecycle node was not activated automatically. Workaround: manually run the lifecycle transition commands.
* The TF tree required a static transform (`map → odom → base_link`) to allow proper visualization in RViz.
* If media files exceed size limits on GitHub, a link is provided instead of large video files.

---

## Submission Checklist

*  Launch files present in `launch/`
*  Configuration files present in `config/`
*  Map files present in `maps/`
*  Demo media included (video or link)
*  README.md updated and descriptive
*  Repository builds successfully using `colcon build`
*  Repository pushed to GitHub and accessible

---

## GitHub Repository for Submission

`https://github.com/<your-github-username>/testbed_navigation1`

A release tag (for example `v1.0`) may also be included to mark the submission version.

Prepared by Keshav Naroju — ERIC Robotics Level 1 ROS2 Navigation Assignment — 2025
