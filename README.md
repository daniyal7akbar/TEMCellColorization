README — TEM Cell Segmentation & Pseudo-Colorization (Multi-Cell U-Net)

Dataset Origin
The dataset originates from:
The Freiburg Electron Microscopy (EM) Dataset – Cell Segmentation Subset
https://lmb.informatik.uni-freiburg.de/data/

Google Drive Dataset Mirror (Prepared by Me)
I have uploaded an organized dataset version (5 cell types) to Google Drive:
https://drive.google.com/drive/folders/1jvZ7mUziVPKFHY-9TbwrZue7R_bkpNpT?usp=drive_link

Expected folder structure:
data/
   BMMC/
   Jurkat/
   hublast/
   prhu/
   J558L/
masks/
   BMMC/
   Jurkat/
   hublast/
   prhu/
   J558L/

Model Architecture
• 5-level Residual U-Net
• Attention Gates
• Dilated Bottleneck
• Dual-Head Output (Segmentation + Colorization)
• Texture-preserving color blending

Training Details
Losses:
• CrossEntropyLoss with class weights [0.05, 1.0, 4.0]
• Dice Loss (50%)
• Smooth L1 Loss for color

Preprocessing:
• CLAHE
• Tight cropping
• Resize to 384×384
• Augmentations

GPU:
Trained using Nvidia GTX 1650 Mobile with 4GB VRAM. Hyperparameters and general training can be changed to accomodate for more or less GPU memory.

Features
• Multi-cell segmentation
• Robust nucleus detection
• Generalizes to unseen TEM images
• Texture-preserving colorization
• Adjustable saturation

Inference
visualize(idx) for dataset samples
<img width="1649" height="541" alt="image" src="https://github.com/user-attachments/assets/6d5ff1a4-ad97-4ce3-a02b-bd14ee028a7a" />

predict_image("img.jpeg") for arbitrary images
<img width="1303" height="626" alt="image" src="https://github.com/user-attachments/assets/dbb1b56a-4bb4-4416-af35-e87a3625768f" />


Use Cases
• Automated cell segmentation
• High-throughput TEM preprocessing
• Nucleus/cytoplasm ratio
• Biological visualization
• Training data generation
• Cross-cell morphology analysis

License
Dataset belongs to Freiburg EM Dataset authors. Can be found at https://lmb.informatik.uni-freiburg.de/data/
Project is for research and educational use.
