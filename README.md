# Water-Surface-Mapping-using-Satellite-Imagery
<img width="1198" height="625" alt="image" src="https://github.com/user-attachments/assets/cc8f6548-8f0e-4de7-ba12-92383bd25d8c" />

This repo is about a pipeline using a foundation model, named Copernicus-FM, to map the water surface from satellite imagery. All info, including the code, the used dataset, and its report, can be found here!

### ABSTRACT:
**Background & gap.** Surface-water mapping underpins flood response, water-security planning, and wetland conservation, yet conventional rule-based indices and task-specific deep networks struggle to generalize across regions and seasons or demand extensive labels. Recent Earth-observation foundation models (FMs) promise transferable representations, but their robustness beyond their pretraining horizon remains under-documented. In particular, the out-of-scope performance of Copernicus-FM on application-driven datasets for water mapping has not been empirically established.

**Method.** We evaluate a frozen Copernicus-FM backbone paired with a lightweight fully-convolutional decoder for binary water-surface segmentation on the Water Bodies dataset. We quantify label efficiency by training with {10, 20, 30, 50, 100}% of the training tiles while keeping validation/test splits fixed. Performance is reported with Overall Accuracy (OA), Intersection-over-Union (IoU), and Dice.

<img width="433" height="233" alt="image" src="https://github.com/user-attachments/assets/82f8a102-94b0-45c6-be07-1ee671f8e3a5" />

**Results.** The model attains Test OA 0.864, IoU 0.749, and Dice 0.855 at full supervision, with strong performance already at 10% labels (IoU 0.683, Dice 0.809). Gains concentrate between 10–30% labels, after which returns saturate; at 30%, the system recovers ~98% of fully-supervised OA/Dice and ~97.5% of IoU. Confusion matrices show decreasing false negatives (12.2%→9.0%) and false positives (5.4%→4.5%), indicating cleaner shoreline and thin-channel delineation. Model size (~13 MB trainable) and inference latency (sub-ms per image) are constant across fractions.

**Discussion & implications.** These findings demonstrate that Copernicus-FM generalizes effectively beyond its pretraining benchmark to an external domain and delivers high-quality water masks with scarce labels, directly addressing concerns about domain specificity. The clear label-efficiency knee (20–30%) provides a practical operating point for rapid, low-cost deployment in resource-constrained regions.

The overview of the architecture of the pipeline proposed in this repo is as follows: 
<img width="1357" height="504" alt="image" src="https://github.com/user-attachments/assets/622ae235-c122-4ada-98fe-79ce79c7c2ef" />

# Getting Started

In this research, we have utilized two notable Python libraries: TorchGeo (for applying Copernicus-FM) and GeoAI (for applying UNet34 trained on ImageNet data), in two distinct environments to avoid any conflicts. To make installation easier, we have added two yml format files that you can call to install all required packages together. "geo311np_environment.yml" for TorchGeo and "geo_environment.yml" for GeoAI. In the following, you can see an example of creating an environment and the installation process for TochGeo:   

- Create a virtual env named "geo311np" and install required packages 
```bash
conda env create -f geo311np_environment.yml --name geo311np
```
- Use the virtual environment
```bash
conda activate geo311np
```
- Open Jupyter notebook
```bash
jupyter notebook
```
[Fraction_WaterBody_CopernicusFM.ipynb](https://github.com/FarFar-Tech/Water-Surface-Mapping-using-Satellite-Imagery/blob/main/Fraction_WaterBody_CopernicusFM.ipynb) includes codes for applying Copernicus-FM, and [Fraction_WaterBody_UNet.ipynb](https://github.com/FarFar-Tech/Water-Surface-Mapping-using-Satellite-Imagery/blob/main/Fraction_WaterBody_UNet.ipynb) includes codes for applying UNet34. You can also find the outputs of the provided codes that we run on our server for both files. They are stored in PDF format with the same names: [Fraction_WaterBody_CopernicusFM.pdf](https://github.com/FarFar-Tech/Water-Surface-Mapping-using-Satellite-Imagery/blob/main/Fraction_WaterBody_CopernicusFM.pdf) and [Fraction_WaterBody_UNet.pdf](https://github.com/FarFar-Tech/Water-Surface-Mapping-using-Satellite-Imagery/blob/main/Fraction_WaterBody_UNet.pdf)   

Server information: 
- Processor	Intel(R) Core(TM) i9-14900HX, 2200 Mhz, 24 Core(s)
- Memory (RAM)	64,0 GB
- NVIDIA GeForce RTX 4090 GPU

# Dataset
We utilize the public Satellite Images of Water Bodies dataset from Kaggle, which was originally compiled from Sentinel-2 imagery and is distributed as 2,841 RGB images paired with 2,841 binary masks (where white represents water and black represents non-water). The collection spans multiple continents, climate zones, and seasons, and includes a broad range of water types (rivers, lakes, ponds, reservoirs, and coastal segments). Masks were produced using a water-index–based procedure (NDWI/MNDWI-style) and manually verified for training use. Figure 2 shows different samples of this data, along with their corresponding masks. The link of the data: 

https://www.kaggle.com/datasets/franciscoescobar/satellite-images-of-water-bodies

<img width="362" height="547" alt="image" src="https://github.com/user-attachments/assets/3f37729a-8650-43a9-8cb0-29ea27a957bb" />

# Contributions
- Robust Water Mapping Beyond Pretraining Scope. We provide the first, to our knowledge, systematic evaluation of Copernicus-FM for surface-water segmentation across two external datasets, demonstrating how FM features transfer to environmental monitoring and flood-related use cases.
- Label-Efficiency Curves with Fixed Validation/Test. We quantify performance across five label budgets (1–100%) using a frozen-backbone + lightweight decoder protocol, showing where returns saturate and what minimum annotation is needed for operational quality. 
- Transparent cost accounting. Beyond accuracy, we report parameter count, model size (MB), training time (s), and inference latency (ms/image) for every fraction. These measurements make the trade-offs between accuracy and cost explicit and actionable for agencies with limited computing or budgets.
- A scalable solution that can be adapted for analyzing additional inputs and for each region targeted by remote sensing researchers and projects.

# Report & Short Video
The report of this research in 11 pages is attached to this repo. It includes sections: Introduction, Methodology, Results, Discussion, and Conclusion. Read it [HERE]()

A short video of presenting this research can be found here: 




