# Technical Approach

## 1. Problem

The existing crushing-detection workflow needed a more useful representation of the area around a sow. Proximity by itself is not enough to determine whether a piglet is in a potentially dangerous position. Sow posture, orientation, segmentation quality and visual occlusion all affect the interpretation of a scene.

## 2. Computer-vision pipeline

The project used YOLO-based segmentation as an input to subsequent computer-vision processing. The segmentation output provided a representation of the sow in each frame.

On top of this, I developed a custom orientation-estimation approach to determine the sow's general head-to-tail direction. The approach was evaluated on footage containing different sows, postures, cameras and recording environments.

**The proprietary algorithm and its implementation details are intentionally not described in this document.** In particular, this overview does not disclose the specific geometric operations, regional comparisons, mask transformations, thresholds or parameter values used by the production-oriented approach.

## 3. Orientation-aware risk representation

The estimated orientation was used as an input to the generation of a more relevant danger-zone representation. The purpose was to distinguish areas around the sow that should not automatically be treated as equally risky.

The work also considered the stability of predictions over time, the effect of partial visibility and the dependency of downstream processing on segmentation quality.

## 4. Evaluation-driven development

Development progressed from exploratory testing to a quantitative evaluation procedure. A labelled ground-truth set was created so that candidate approaches could be compared against reference orientation labels.

Results were examined across individual recordings and postures rather than relying only on one aggregate score. This helped identify cases where performance was affected by upstream segmentation quality or recording conditions.

## 5. Edge deployment

Deployment suitability was investigated on NVIDIA Jetson hardware. YOLO inference was optimized using NVIDIA TensorRT, alongside broader pipeline optimization. Testing showed that improving model inference does not necessarily increase end-to-end throughput indefinitely: camera capture and the surrounding processing pipeline can become limiting factors.

## 6. Engineering considerations

The development process considered:
- Accuracy across standing and lying postures.
- Stability across consecutive video frames.
- Partial visibility and segmentation quality.
- Computational constraints of edge hardware.
- Integration with the existing event-processing workflow.
- The difference between component-level accuracy and end-to-end detection performance.

## 7. Confidentiality boundary

This document is a high-level portfolio description. It intentionally omits the proprietary orientation-estimation procedure and exact danger-zone construction method. No source code, implementation pseudocode, internal screenshots, farm footage or sensitive deployment configuration is included.
