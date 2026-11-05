# System Architecture — High-Level Overview

This document describes the system at a component level. It is not an internal architecture specification and intentionally avoids company-specific diagrams, deployment topology, credentials, network details and implementation-level interfaces.

## Components

### 1. Camera input
A camera provides video footage of the farrowing environment. The footage is used as input for the computer-vision workflow.

### 2. Edge processing
An NVIDIA Jetson device runs the computer-vision workload close to the camera. YOLO-based detection and segmentation provide visual information for subsequent processing. TensorRT and other optimization techniques were investigated to improve inference performance on the edge device.

### 3. Computer-vision processing
Custom processing uses the model output to estimate sow orientation and generate a more relevant risk-area representation. The exact algorithmic implementation is proprietary and is therefore not documented here.

### 4. Event communication
When the detection workflow produces an event, it can be represented as structured event data and communicated to backend services. The project investigated event-driven communication and controlled integration testing.

### 5. Backend and persistence
Backend services receive and process event information. Supabase was used in the prototype for structured data storage. Media handling was considered separately from event metadata.

### 6. Dashboard
The dashboard consumes stored event information and presents events and statistics in a form that can be reviewed by users.

## Conceptual data flow

```text
Camera footage
      |
      v
Edge device (NVIDIA Jetson)
      |
      v
YOLO-based detection / segmentation
      |
      v
Custom computer-vision processing
      |
      v
Structured detection event
      |
      v
Backend / event communication
      |
      v
Database and media storage
      |
      v
Dashboard and visualization
```

This is a conceptual view of the processing stages, not a reproduction of BaiTech's internal architecture diagram.

## Integration testing

A controlled test setup was developed to validate the downstream pipeline without depending on real crushing events. A known physical input could be used to generate a representative event, which was then followed through event communication, backend processing, storage and dashboard presentation.

The key principle was to test the event interface and downstream workflow independently from the internal computer-vision algorithm. This made the integration path repeatable and easier to troubleshoot.

## Technologies referenced

- NVIDIA Jetson
- Ultralytics YOLO
- NVIDIA TensorRT
- Python and computer-vision libraries
- NATS and REST-based communication in the wider prototype/testing context
- Supabase
- BigLife dashboard

The exact deployment configuration and internal service topology are intentionally excluded.
