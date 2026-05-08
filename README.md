# deeplearning-project

# Deep Learning Project for Forest Fire Detection

## Overview
This project investigates the use of dehazing as a preprocessing step to improve forest fire detection in degraded weather conditions, particularly under haze. The main objective is to evaluate if dehazing techniques, such as the proposed PGAD-Net v2 (Physics-Guided Attention Dehazing Network), can enhance the performance of fire detection models when smoke and haze are present.

The proposed method, PGAD-Net v2, integrates a learned encoder-decoder architecture with a spatially-aware physics attention gate based on the Dark Channel Prior, aimed at improving the clarity of images affected by haze. The project evaluates dehazing on datasets such as RESIDE-6K, O-HAZE, and D-Fire to explore its effects on both image restoration quality and downstream fire detection performance.

## GitHub Repository
[GitHub Repository](https://github.com/mishalzaidi/deeplearning-project)

## Dataset
- **RESIDE-6K**: A benchmark dataset of 6,000 synthetically hazy and clean outdoor images.
- **O-HAZE**: A real outdoor haze dataset containing 45 paired hazy and clean images.
- **D-Fire**: A dataset for fire and smoke detection, containing 21,527 annotated fire and smoke images, with a focus on detecting fire and smoke in clean conditions.

## Requirements
- Python 3.x
- TensorFlow / PyTorch 
- OpenCV
- NumPy
- Matplotlib

## Installation
git clone https://github.com/mishalzaidi/deeplearning-project.git
cd deeplearning-project

## Methodology 
1.Dehazing as a Preprocessing Step: This project investigates if dehazing can improve fire detection performance when haze or smoke is present. We utilize the PGAD-Net v2 model, which is a hybrid model combining CNN-based encoder-decoder architecture and physics-guided attention gates based on the Dark Channel Prior.
2.Two-Stage Training: The model is trained in two stages:
Stage 1: Pretraining on the RESIDE-6K dataset, which consists of synthetic hazy and clean images.
Stage 2: Fine-tuning on the O-HAZE dataset to adapt to real-world haze.
3.Fire Detection: After dehazing, the processed images are passed through a YOLOv8n detector trained on clean D-Fire images. The evaluation compares the performance of dehazed images against hazy and clean inputs.

## Results
Dehazing Performance: PGAD-Net v2 improves image quality in both synthetic and real haze scenarios, with a notable improvement in PSNR and SSIM on O-HAZE dataset.
Detection Performance: Despite improved image quality, dehazing reduces detection performance, especially for smoke. The recall decreases due to the similarity between haze and smoke in the dehazed images.

## Architecture 
PGAD-Net v2 is a hybrid architecture:

Encoder: A three-layer CNN maps the hazy input to feature representations.
Physics Attention Gate: The Dark Channel Prior is used to compute a haze density map, which is used to modulate the feature space.
Residual Refinement: Features are further refined using residual blocks with channel attention.
Decoder: The refined features are mapped back to the image space, with a skip connection to the input to minimize the reconstruction error.

## Conclusion
The project demonstrates that dehazing as a preprocessing step does not improve fire and smoke detection performance. In fact, dehazing in some cases negatively impacts the recall, especially for smoke detection. The findings emphasize the importance of task-aware dehazing, where the dehazing model is trained jointly with the detector to preserve important features for detection.

## Future Directions
Task-aware dehazing: Training the dehazing model together with the detector.
Larger real-world haze datasets for better generalization.
Multi-modal sensing approaches combining RGB imagery with thermal or smoke sensors for more robust early detection.

## Acknowledgments
The authors would like to acknowledge the contributions of the RESIDE-6K, O-HAZE, and D-Fire datasets.
Special thanks to the developers of PGAD-Net and YOLOv8 for their work on the dehazing and detection models used in this project.
