# ROS TurtleBot3 and RGB-D Camera Integration

This repository documents my internship project at **ZTE – Multimedia University (MMU)**, where I integrated an **RGB-D depth camera** with a **TurtleBot3 (TB3)** robot using ROS. The project demonstrates how to combine LiDAR-based mapping with RGB-D vision for both **static mapping** and **dynamic 3D perception** during autonomous navigation.

---

## 🚀 Project Overview
The project is divided into two main parts:

### 1. Static Map (LiDAR-based SLAM)
- Launch SLAM using **Gmapping** to create a 2D occupancy grid map.
- Visualize in **RViz** and teleoperate TB3 for exploration.
- Save the generated map as `.pgm` and `.yaml`.
- Perform autonomous navigation using the saved static map.

### 2. Dynamic Map (Depth Camera Integration)
- Integrate an **RGB-D camera** with ROS Noetic.
- Use `depthimage_to_laserscan` to convert depth images into laser scan data.
- Merge laser scans from **LiDAR** and **depth camera** using a custom `scan_merger.py` node.
- Visualize **PointCloud2** and **DepthCloud** topics in RViz for 3D perception.
- Adjust camera transforms (x, y, z, roll, pitch, yaw) for accurate alignment.

---

## 🛠️ Tools & Dependencies
- **ROS Noetic** (ROS 1)  
- **TurtleBot3 Packages**  
- **depthai-ros** (Luxonis OAK-D / RGB-D camera integration)  
- **depthimage_to_laserscan**  
- **Laserscan Multi Merger**  
- **RViz**  

---

## 📂 Repository Contents
- `slam_setup/` → Steps and configs for LiDAR-based mapping.  
- `rgbd_integration/` → Depth camera integration setup.  
- `scan_merger.py` → Script to merge LiDAR and RGB-D laser scans.  
- `launch_files/` → Modified launch files for SLAM and navigation.  
- `docs/` → Guide and diagrams from the internship project.  

---

## 📖 Usage
1. **Bring up TurtleBot3**  
   ```bash
   roslaunch turtlebot3_bringup turtlebot3_robot.launch
   ```

2. **Run LiDAR-based SLAM**  
   ```bash
   roslaunch turtlebot3_slam turtlebot3_slam.launch
   ```

3. **Launch Depth Camera Node**  
   ```bash
   roslaunch depthai_examples stereo_inertial_node.launch
   ```

4. **Run Depth to Laser Conversion**  
   ```bash
   rosrun depthimage_to_laserscan depthimage_to_laserscan image:=/camera/depth/image_raw
   ```

5. **Merge LiDAR + Camera Laser Scans**  
   ```bash
   python3 scan_merger.py
   ```

6. **Visualize in RViz**  
   Add `/scan`, `/laser_scan`, and `/pointcloud2` topics.

---

## 📊 Results
- Generated **2D maps** using LiDAR and RGB-D laser scans.  
- Achieved **dynamic navigation** with 3D visualization in RViz.  
- Demonstrated real-time integration of multiple sensors for autonomous robots.  

---

## 📌 Acknowledgments
- Internship at **ZTE – Multimedia University (MMU)**.  
- Supervisor and team for technical guidance.  
- Open-source ROS community (DepthAI, TurtleBot3, ROS Wiki).  

---

## 📜 License
This project is open-sourced under the **MIT License**.
