# Computer Vision for Sow Orientation and Piglet-Crushing Detection

**Graduation project | BaiTech B.V. — BigLife | 2026**

This repository presents a public-facing overview of my graduation project at BaiTech B.V. The work focused on improving an existing camera-based piglet-crushing detection system by developing and evaluating computer-vision functionality for sow orientation estimation and danger-zone generation. The project also included edge-deployment optimization and end-to-end integration testing.

> **Confidentiality notice:** This repository intentionally describes the solution at a high level. Proprietary algorithmic implementation details, internal diagrams, application screenshots, source code, farm footage, datasets and confidential infrastructure information are not included.

## Project at a glance

Piglet-crushing detection is challenging because proximity alone does not indicate risk. Piglets may be close to a sow without being in a dangerous position. The project addressed a limitation in an existing system by adding information about sow orientation and posture to support a more relevant risk area.

The work covered:
- Computer-vision development using YOLO-based segmentation.
- Development and evaluation of a custom sow-orientation estimation approach.
- Generation of an orientation-aware danger-zone representation.
- Evaluation across multiple recordings, cameras and sow postures.
- Edge deployment testing and inference optimization on NVIDIA Jetson hardware.
- Integration testing across device processing, backend communication, data storage and dashboard visualization.

## Evaluation highlights

| Evaluation | Result |
|---|---:|
| Orientation evaluation set | 13,015 labelled frames |
| Recordings | 12 videos |
| Camera coverage | 9 cameras across multiple farm environments |
| Overall orientation accuracy | **98.66%** |
| Standing orientation accuracy | 97.94% |
| Lying orientation accuracy | 99.17% |

Only five sitting frames were present in the labelled orientation dataset. The 100% sitting result should therefore not be interpreted as a reliable estimate of performance for that posture.

A separate limited test of the wider crushing-detection system recorded:
- **87% detection** across 23 confirmed crushing-event clips (20 detected).
- **90% correct rejection** across 20 selected non-crushing clips (18 correctly rejected).

These are results from a limited test set, not a claim of production-level performance or an established reduction in piglet mortality. The two evaluations measure different parts of the system and should not be conflated.

## System overview

At a high level, the solution connects the following stages:

1. Camera footage is processed on an edge device.
2. YOLO-based computer vision provides animal detection and segmentation information.
3. Custom computer-vision processing estimates sow orientation and supports the generation of a more relevant danger-zone representation.
4. Detection events are converted into structured event data.
5. The backend receives and processes events, while database and media storage retain relevant information.
6. A dashboard presents event information and monitoring statistics.

The wider prototype used NVIDIA Jetson hardware, TensorRT optimization, NATS messaging, Supabase storage and a dashboard. The documentation explains the roles of these components without exposing internal deployment diagrams or configuration.

## Technology

- **Programming and computer vision:** Python, OpenCV, Ultralytics YOLO
- **Model deployment:** NVIDIA Jetson, NVIDIA TensorRT
- **Backend and event integration:** REST APIs, NATS
- **Data storage:** Supabase
- **Visualization:** Web dashboard
- **Evaluation:** Ground-truth labelling, quantitative testing and video-based validation

## My contribution

My work included:
- Investigating the causes of unreliable crushing-risk localization.
- Developing and comparing computer-vision approaches for sow orientation estimation.
- Creating a labelled evaluation procedure and analysing performance across recordings and postures.
- Integrating orientation information into danger-zone generation.
- Investigating temporal consistency and robustness under challenging visual conditions.
- Testing and optimizing model deployment on edge hardware.
- Building and validating an end-to-end test path from camera/device input through backend processing and storage to dashboard visualization.

## Repository contents

- [`documentation/project-overview.md`](documentation/project-overview.md) — context, objective, scope and contribution.
- [`documentation/technical-approach.md`](documentation/technical-approach.md) — public-facing description of the computer-vision approach.
- [`documentation/system-architecture.md`](documentation/system-architecture.md) — high-level component roles and data flow.
- [`documentation/results-and-evaluation.md`](documentation/results-and-evaluation.md) — evaluation setup, results and limitations.
- [`presentations/`](presentations/) — adapted presentations suitable for public sharing.

## Limitations and responsible interpretation

The project evaluated orientation estimation and tested selected crushing and non-crushing clips. It did not establish a causal reduction in piglet mortality, nor did the limited clip evaluation establish production-wide precision and recall. Performance depends on upstream segmentation quality, animal posture, visibility, occlusion, camera conditions and the representativeness of evaluation data.

## About

Graduation project completed at **BaiTech B.V.**, contributing to the **BigLife** camera-based livestock monitoring system.

This repository is intended as a project portfolio and documentation resource. It does not contain the proprietary implementation or operational assets.
