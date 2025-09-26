# Water-Surface-Mapping-using-Satellite-Imagery
<img width="1198" height="625" alt="image" src="https://github.com/user-attachments/assets/cc8f6548-8f0e-4de7-ba12-92383bd25d8c" />

This repo is about a pipeline using a foundation model, named Copernicus-FM, to map the water surface from satellite imagery. All info, including the code, the used dataset, and its report, can be found here!

### ABSTRACT:
**Background & gap.** Surface-water mapping underpins flood response, water-security planning, and wetland conservation, yet conventional rule-based indices and task-specific deep networks struggle to generalize across regions and seasons or demand extensive labels. Recent Earth-observation foundation models (FMs) promise transferable representations, but their robustness beyond their pretraining horizon remains under-documented. In particular, the out-of-scope performance of Copernicus-FM on application-driven datasets for water mapping has not been empirically established.

**Method.** We evaluate a frozen Copernicus-FM backbone paired with a lightweight fully-convolutional decoder for binary water-surface segmentation on the Water Bodies dataset. We quantify label efficiency by training with {10, 20, 30, 50, 100}% of the training tiles while keeping validation/test splits fixed. Performance is reported with Overall Accuracy (OA), Intersection-over-Union (IoU), and Dice.

**Results.** The model attains Test OA 0.864, IoU 0.749, and Dice 0.855 at full supervision, with strong performance already at 10% labels (IoU 0.683, Dice 0.809). Gains concentrate between 10–30% labels, after which returns saturate; at 30%, the system recovers ~98% of fully-supervised OA/Dice and ~97.5% of IoU. Confusion matrices show decreasing false negatives (12.2%→9.0%) and false positives (5.4%→4.5%), indicating cleaner shoreline and thin-channel delineation. Model size (~13 MB trainable) and inference latency (sub-ms per image) are constant across fractions.

**Discussion & implications.** These findings demonstrate that Copernicus-FM generalizes effectively beyond its pretraining benchmark to an external domain and delivers high-quality water masks with scarce labels, directly addressing concerns about domain specificity. The clear label-efficiency knee (20–30%) provides a practical operating point for rapid, low-cost deployment in resource-constrained regions.

The overview of the architecture of the pipeline proposed in this repo is as follows: 
<img width="1357" height="504" alt="image" src="https://github.com/user-attachments/assets/622ae235-c122-4ada-98fe-79ce79c7c2ef" />


