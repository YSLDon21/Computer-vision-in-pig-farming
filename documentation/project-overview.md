# Project Overview

## Context

BaiTech B.V. develops technology for livestock monitoring through the BigLife platform. One application of camera-based monitoring is identifying situations in which piglets may be at risk of being crushed by a sow.

The project addressed a challenge in an existing computer-vision pipeline: a piglet being close to a sow does not necessarily mean that it is in a dangerous position. A more useful risk representation requires context about the sow's posture and orientation.

## Objective

The main objective was to improve the reliability of the spatial information used by an existing piglet-crushing detection system. The work focused on estimating the sow's head-to-tail orientation from top-down camera footage and using that information to support a more relevant danger-zone representation.

A second workstream investigated how detection events could be tested end to end, from an edge device through backend services and storage to dashboard visualization.

## Scope

The project included:
- Computer-vision development based on YOLO segmentation.
- Sow orientation estimation and evaluation.
- Danger-zone generation using orientation information.
- Evaluation across multiple recordings, cameras and postures.
- Edge-hardware deployment and inference optimization.
- Integration testing of event communication, storage and dashboard presentation.

The project did not replace the complete BigLife platform or independently establish a reduction in piglet mortality.

## My contribution

I investigated the technical problem, developed and compared orientation-estimation approaches, created a ground-truth evaluation procedure, analysed failure cases and integrated the resulting orientation information into the wider detection workflow. I also investigated edge deployment optimization and developed an end-to-end test setup for the device-to-dashboard path.

## Outcome

The orientation approach achieved 98.66% overall accuracy on the labelled evaluation set of 13,015 frames. The work also demonstrated an integration path connecting edge-device processing, backend event handling, data storage and dashboard visualization.

## Project context

- **Organization:** BaiTech B.V.
- **Product context:** BigLife
- **Project type:** Graduation project
- **Period:** May–November 2026
