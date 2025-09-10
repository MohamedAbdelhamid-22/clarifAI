Model Comparison for Video-Based Emotion Detection
| **Model**                                    | **Accuracy** (FER2013 / AffectNet / Custom) | **Speed**                                | **Size**   | **Pros**                                                                    | **Cons**                                                                | **Video Suitability**                        |
| -------------------------------------------- | ------------------------------------------- | ---------------------------------------- | ---------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------- | -------------------------------------------- |
| **VGG16 (Baseline)**                         | Medium                                      | Medium                                   | Large      | Easy to train, solid baseline                                               | Heavy, slow on CPU, no temporal awareness                               | **OK** (needs smoothing)                     |
| **Mini-Xception**                            | Medium                                      | **Fast**                                 | Small      | Lightweight, real-time capable                                              | Slightly lower accuracy                                                 | **Very Good** for real-time                  |
| **ResNet-50 (Fine-Tuned)**                   | High                                        | Medium                                   | Large      | Robust, higher accuracy                                                     | Needs GPU, heavier than Mini-Xception                                   | **Good** but slower                          |
| **VGG19 (Fine-Tuned)**                       | Good                                        | Slow                                     | Very Large | Strong feature extraction                                                   | Too heavy for real-time                                                 | **Poor**                                     |
| **DeepFace**                                 | Medium                                      | Medium                                   | Medium     | Plug-and-play, multi-task (age, gender, emotion)                            | Limited customization, frame-based                                      | **Limited**                                  |
| **CNN + LSTM (Temporal)**                    | High                                        | Slower                                   | Medium     | Captures temporal patterns, smooth predictions                              | Needs more data, harder to implement                                    | **Best** for trends over time                |
| **I3D / TimeSformer (3D CNN / Transformer)** | Very High (SOTA)                            | Slow (GPU needed)                        | Very Large | Captures spatiotemporal features                                            | Complex, resource-heavy                                                 | **Advanced Best**                            |
| **YOLO + Emotion Classifier**                | High (if combined with ResNet/Xception)     | **Very Fast** (real-time, GPU-optimized) | Medium     | Detects faces + assigns IDs, works well for multi-person tracking, scalable | Requires extra emotion classifier, YOLO alone doesn’t classify emotions | **Excellent** for classroom/student tracking |

🔑 Key Notes on YOLO

Why useful?
Unlike other models, YOLO can detect multiple faces quickly and assign bounding boxes/IDs.
Then you can pipe each cropped face into an emotion classifier (ResNet/Mini-Xception).

Strength: Handles multi-student classroom videos better than standalone CNN models.

Best combo: YOLO for detection + ResNet/Mini-Xception for classification = speed + accuracy.

Limitation: YOLO itself doesn’t predict emotions, only detects/locates faces.
