# 🤖 Task-Registered Robotic Welding Framework

A task-registered multi-chain synthetic-data framework for **sim-to-real visual perception and downstream weld-path generation in robotic rebar-to-plate welding**.

This research investigates how synthetic data can be expanded across appearance and structural variations while preserving the task semantics, geometric information, and robot states required for downstream robotic execution.

> 📄 A manuscript based on this project is currently under preparation/submission.  
> Selected materials are presented here as a research portfolio. Full code and datasets will be released with the corresponding publication.

---

## 🔍 Overview

Robotic welding in semi-structured environments is challenging because metallic reflections, rust, illumination changes, occlusions, and structural variations can cause large domain gaps between simulation and real-world images.

This project develops a **task-registered synthetic-data pipeline** in NVIDIA Isaac Sim. Each registered observation links:

- intensity images
- semantic masks
- numerical depth
- point clouds
- camera parameters
- robot states
- task-object identities

This registration makes it possible to modify image appearance or scene structure while maintaining a traceable relationship between visual data, supervision, 3D geometry, and robot configuration.

---

## 🧠 Framework

The overall workflow is:

```text
Parameterized Isaac Sim Workcell
                ↓
       Registered Source State
                ↓
 ┌──────────────┴──────────────┐
 │                             │
Appearance Expansion     Structural Expansion
 │                             │
 ↓                             ↓
PhotoReal-Multi          Scene-Rand
PhotoReal-Diverse             │
 │                             ↓
 └──────────────→        Joint-Multi
                ↓
       Semantic Segmentation
                ↓
          Real-Image Evaluation
                ↓
      RGB-D Geometry Recovery
                ↓
         3D Weld Paths
                ↓
     Robot Interface Checking
