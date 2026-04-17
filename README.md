# lidar-perception-annotation-pipeline
📌 Overview

This project focuses on improving the data quality pipeline for autonomous vehicle (AV) perception systems, specifically targeting LiDAR-based datasets.

Accurate perception in AVs depends heavily on high-quality annotated data. However, manual annotation of LiDAR point clouds is:

Time-consuming
Error-prone
Highly inconsistent

This project proposes a streamlined annotation and validation workflow, combined with class imbalance mitigation techniques, to produce more reliable training datasets for perception models.

🎯 Objectives
Develop an efficient LiDAR annotation and review workflow
Automate dataset validation using Python
Identify and mitigate class imbalance issues
Evaluate impact on perception model performance
🧠 Key Concepts
Semantic Segmentation (point-wise classification)
Object Detection (bounding boxes using YOLO)
Class Imbalance in long-tail datasets
Dataset validation and quality assurance
Data-centric AI (improving data instead of just models)
⚙️ System Pipeline
Data Collection → Annotation → Review → Validation → Dataset Analysis → Model Training → Evaluation

Tools Used
LiDAR datasets (nuScenes / SemanticKITTI format)
J. Behley Labeller (point cloud annotation)
BasicAI (annotation review platform)
Python (NumPy, data analysis scripts)
YOLO-based detection models
🛠️ Methodology
1. Annotation & Review
Annotated LiDAR point clouds using tile-based segmentation
Reviewed annotations using structured guidelines
Identified:
Duplicate objects
Misclassified labels
Missing detections

📌 Example issues:

Duplicate pedestrian annotations
Incorrect visibility attributes
Missed detections due to camera blind spots
2. Automated Validation

Custom Python scripts were developed to:

Count class distributions
Detect anomalies (missing/rare classes)
Generate CSV summaries for analysis

This reduces reliance on manual inspection and improves consistency.

3. Class Imbalance Analysis

Dataset showed long-tail distribution:

Dominant classes: car, adult
Rare classes: police_officer, child, debris

This imbalance leads to:

Poor detection of rare but critical objects
Biased model performance
4. Mitigation Strategies
A. Focal Loss (Algorithm-Level)
Designed to focus on hard examples
Result:
Slight precision increase
Overall performance decreased
Poor improvement for rare classes
B. Targeted Augmentation (Data-Level)
Increased samples for minority classes
Controlled augmentation intensity per class

Result:

Dataset size increased by ~32%
Significant boost in minority class representation
📊 Results
Baseline Model
Precision: 0.79
Recall: 0.55
mAP@0.5: 0.63

Problem:

High precision, low recall → missing objects
Focal Loss
Slightly higher precision
Lower recall and mAP

❌ Conclusion:
Focal loss alone does not solve class imbalance effectively

Targeted Augmentation (Best Result)
Precision: 0.84
Recall: 0.64
mAP@0.5: 0.74
mAP@0.5:0.95: 0.52

✅ Improvements:

Better detection coverage
Stronger localisation
Significant gains for minority classes
📈 Key Insights
Data quality > model complexity
Annotation errors directly degrade model performance
Class imbalance is a major bottleneck in AV perception
Data-level solutions outperform algorithm-only approaches
Combining validation + augmentation yields best results
🧪 Project Contributions
Designed a semi-automated LiDAR annotation workflow
Developed Python-based validation tools
Implemented class-aware augmentation strategy
Provided quantitative comparison of mitigation methods
🚀 Future Improvements
Integrate full 3D detection models (not just 2D YOLO)
Extend to multi-sensor fusion (camera + LiDAR)
Improve detection of small/rare objects (e.g. child class)
Deploy pipeline in real-time AV systems
📷 Sample Outputs

(Add your screenshots here — this is very important)

Annotated point clouds
Bounding box detection results
Class distribution graphs
📂 Project Structure
├── src/                # Core scripts
├── data/               # Sample dataset (or link externally)
├── results/            # Outputs and visualisations
├── models/             # Trained weights (optional)
├── docs/               # Diagrams and report
├── requirements.txt
└── README.md

📎 Dataset
nuScenes / nuScenes-mini
SemanticKITTI format

(Provide download link instead of uploading full dataset)

👨‍💻 Authors
Gabriel Tan Jun Cong
Cheng Jai Qhuen
🏫 Institution

Ngee Ann Polytechnic – Engineering Science

🧾 Conclusion

This project demonstrates that improving annotation quality and dataset balance significantly enhances perception model performance.

Rather than relying solely on model architecture, a data-centric approach provides a more effective and scalable solution for autonomous vehicle systems.
