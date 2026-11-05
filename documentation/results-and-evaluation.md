# Results and Evaluation

## 1. Sow orientation evaluation

The orientation-estimation work was evaluated using manually established ground-truth labels.

### Evaluation dataset

| Characteristic | Value |
|---|---:|
| Recordings | 12 videos |
| Total footage | 11 minutes 20 seconds |
| Cameras | 9 |
| Labelled frames | 13,015 |
| Lying frames | 7,620 |
| Standing frames | 5,390 |
| Sitting frames | 5 |

### Main result

The selected orientation-estimation approach achieved **98.66% overall accuracy** on the evaluated dataset.

| Posture | Accuracy |
|---|---:|
| Standing | 97.94% |
| Sitting | 100%* |
| Lying | 99.17% |
| **Overall** | **98.66%** |

*The sitting category contained only five labelled frames. Its score is therefore not statistically representative and should be interpreted cautiously.*

The evaluation was also reviewed per recording and posture. This matters because a single aggregate score can hide weaknesses associated with particular animals, postures, camera views or segmentation conditions.

## 2. Wider crushing-detection clip test

A separate limited test was performed on the wider crushing-detection system.

| Test group | Correct outcomes | Total | Result |
|---|---:|---:|---:|
| Confirmed crushing-event clips detected | 20 | 23 | **87%** |
| Non-crushing clips correctly rejected | 18 | 20 | **90%** |

These figures describe a small selected clip test. They are not equivalent to a comprehensive production evaluation, and they should not be interpreted as production-wide precision, recall or a demonstrated reduction in piglet mortality.

The test also highlighted areas for further development, including posture classification, animal occlusion and identity continuity, segmentation quality for visually varied animals, and environmental objects that can affect detections.

## 3. Edge deployment

Deployment testing was performed on NVIDIA Jetson hardware. TensorRT optimization substantially reduced model inference time. Additional pipeline optimization improved processing performance, while later tests indicated that camera capture could become a limiting factor.

This demonstrated the importance of measuring end-to-end performance rather than considering neural-network inference time in isolation.

Exact device configurations and detailed performance tuning parameters are not included in this public overview.

## 4. Integration outcome

A controlled integration-testing workflow was developed to validate the path from a physical input on an edge device to event processing, storage and dashboard visualization.

This provided a repeatable way to test downstream functionality without waiting for real-world crushing events.

## 5. Limitations

- The orientation dataset contained only five sitting frames.
- Orientation accuracy measures the orientation component, not the full crushing-detection system.
- The crushing/non-crushing clip test was limited in size and scope.
- Detection quality depends on upstream segmentation, visibility, occlusion, camera conditions and animal appearance.
- The project did not establish a causal effect on piglet mortality.
- Further evaluation with a larger, representative set of labelled real-world events would be required for stronger end-to-end conclusions.

## 6. Interpretation

The results support the feasibility of estimating sow orientation from the available computer-vision input with high accuracy on the evaluated footage. They also show why component-level metrics and end-to-end system metrics must be reported separately.

The project combined quantitative evaluation, failure-case analysis, edge deployment testing and integration validation to assess the solution beyond a single model score.
