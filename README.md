# AI-or-Real: ML Classification

## Project Overview

The "AI-or-Real" project aims to tackle the growing challenge of distinguishing AI-generated images from real-world images. With advancements in image synthesis technologies like Generative Adversarial Networks (GANs), the line between real and artificial has blurred. This project utilizes machine learning techniques to develop a robust classifier capable of identifying the authenticity of images with high accuracy.

---

## Motivation

The ability to differentiate between real and AI-generated images is essential for maintaining authenticity in digital media, journalistic integrity, and cybersecurity. As AI-generated content becomes more pervasive, the potential for misuse grows, necessitating reliable tools for verification.

Key use cases include:
- Content moderation on social media platforms.
- Verifying the authenticity of journalistic content.
- Ensuring the reliability of digital evidence in legal contexts.

---

## Objectives

1. **Develop a Classifier Model**: Implement a machine learning model leveraging state-of-the-art techniques to classify images as real or AI-generated.
2. **Achieve High Accuracy**: Aim for a benchmark accuracy of 90% or higher on testing datasets.
3. **Controlled Dataset Analysis**: Use a dataset of apple images to control variables and analyze model performance under simplified conditions.
4. **Establish a Framework for Future Research**: Create a scalable methodology adaptable to broader datasets and applications.

---

## Dataset

### Real Images:
- Collected from various sources, including photos taken manually and images downloaded from platforms like Pinterest.

### AI-Generated Images:
- Generated using tools like DALL-E, Gemini, and MidJourney.
- Different prompts were employed to ensure variability and reduce model bias.

### Preprocessing:
- All images were cropped to square shapes and downscaled to 192x192 pixels.
- Shadow characteristics were analyzed using the SBU Shadow Dataset.

---

## Methodology

### Identification of Key Inconsistencies:
- **Lighting and Shadows**: AI-generated images often show unnatural light and shadow patterns.
- **Texturing and Color**: Unnatural textures and color gradients are common in synthetic images.
- **Background Inconsistencies**: Objects and their backgrounds may lack spatial coherence.
- **Lack of Digital Noise**: AI-generated images typically lack realistic noise patterns.

### Feature Engineering:
- Employed "Direction-Aware Spatial Context Features for Shadow Detection and Removal" ([Wang et al., 2018](https://arxiv.org/abs/1805.04635)).
- Generated shadow masks to evaluate the consistency of light and shadow elements.

### Model Architecture:
- A Convolutional Neural Network (CNN) with the following layers:
  - Three convolutional layers (3x3 kernel) with 2x2 pooling layers.
  - Flatten layer to convert feature maps into a single vector.
  - Dense layer with L2 regularization and a dropout rate of 0.7.
  - Sigmoid output layer for binary classification (real vs. AI-generated).

### Training and Validation:
- An 80/20 train-validation split was used.
- The model achieved training accuracy of 90% and validation accuracy of ~86%.

---

## Results

- **Testing Metrics**:
  - Accuracy: 90%
  - Precision: 86%
  - Recall: 95%
  - F1 Score: 0.90
  - AUC-ROC: 0.96

- **Key Insights**:
  - Shadow analysis improved base accuracy from 75% to 90%.
  - Validation metrics exhibited fluctuations, suggesting potential overfitting and challenges with highly realistic synthetic images.

---

## Challenges

1. **Dataset Variability**: AI-generated images vary significantly in quality, introducing complexity during model training.
2. **Subtle Inconsistencies**: Realistic synthetic images remain challenging to identify consistently.
3. **Overfitting**: The model showed fluctuations in validation performance, highlighting areas for further refinement.

---

## Future Work

1. **Expand Dataset Diversity**:
   - Include varied subjects and environments to improve model robustness.
   - Address subtle inconsistencies in highly realistic images.

2. **Integrate Additional Features**:
   - Analyze textural anomalies, unnatural gradients, and digital noise patterns.

3. **Develop Unified Models**:
   - Transition from a pipeline approach to a single comprehensive model capable of handling all features concurrently.

4. **Broader Applications**:
   - Adapt the model for other AI-generated content, including videos and 3D renderings.

---

## References

1. Wang, H., Zhu, Z., Fu, H., Qin, J., & Heng, P. A. (2018). "Direction-Aware Spatial Context Features for Shadow Detection and Removal." [arXiv:1805.04635](https://arxiv.org/abs/1805.04635).
2. SBU Shadow Dataset: Stonybrook University. [SBU Dataset](https://www3.cs.stonybrook.edu/~cvl/projects/shadow_noisy_label/index.html).

