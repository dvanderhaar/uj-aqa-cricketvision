# Dataset

The **UJ-AQA-CricketVision** dataset is the first publicly available Action Quality Assessment (AQA) dataset for cricket batting. It contains **8,182 annotated batting video clips** collected from international cricket footage and is designed to support research in Action Quality Assessment, computer vision, pose estimation, sports analytics, and cricket coaching. The dataset and its construction are described in our WACV publication.

## Dataset Contents

The repository contains both the **video clips** and the corresponding **annotation files**.

### Videos

The dataset consists of **8,182 short video clips**, where each clip represents a single cricket batting stroke.

Each clip contains:

- One complete batting action
- Three annotated phases:
  - Buildup
  - Execution
  - Follow-through
- Front-foot and back-foot strokes
- Left- and right-handed batters
- Six batting stroke categories:
  - Off Drive
  - On Drive
  - Cut / Square Drive
  - Glance
  - Hook
  - Block

The videos are organised into folders according to their batting attributes, making it easy to locate samples for specific experiments.

---

## Annotation Files

Each video has an associated JSON annotation containing all metadata required for training and evaluation.

The annotation files include:

- Video filename
- Stroke type
- Foot type
- Batter handedness
- Phase timestamps
- Bounding box coordinates
- Overall action quality score
- Individual body-part scores
  - Head
  - Shoulders
  - Hands
  - Hips
  - Feet
- Additional metadata captured during annotation

The JSON annotations can be downloaded directly from GitHub together with the corresponding videos.

---

## Repository Structure

```text
CricketVision_dataset_release/
│
├── JSON.zip/
│   ├── P1_V1/
│   └── ...
│
├── Videos.zip/
│   ├── P1_V1
│   ├── ...
│
├── scoring_guideline/
│
└── README.md
```

---

## Using the Dataset

Clone the repository:

```bash
git clone https://github.com/dvanderhaar/uj-aqa-cricketvision.git
```

The videos can be accessed directly from the `CricketVision_dataset_release/videos.zip` directory, while the accompanying JSON files provide the annotations required to identify the stroke type, batting attributes, phase locations, quality scores, and other metadata for each sample.

The annotation files are stored in a standard JSON format and can be loaded easily in Python:

```python
import json

with open("annotations/dataset.json", "r") as f:
    annotations = json.load(f)

print(annotations[0])
```

Each JSON record corresponds to a single video clip (can be downloaded under dataset release), allowing researchers to directly link the annotations with the associated batting video for training, evaluation, or further analysis.

# Dataset Statistics

## Overall Competency Distribution

The dataset contains **8,182** batting samples, with each sample assigned a competency score between **0** (poor) and **10** (excellent).

| Competency Range | Description | Number of Samples |
|-----------------|-------------|------------------:|
| 0–3 | Poor | 1,497 |
| 4–6 | Average | 2,391 |
| 7–8 | Good | 2,516 |
| 9–10 | Excellent | 1,778 |
| **Total** | | **8,182** |

---

# Back Foot Shots

The table below summarises the distribution of **back foot** batting shots by handedness and stroke type.

| Stroke ID | Stroke | Left-Handed | Right-Handed | Total Samples |
|-----------|--------|------------:|-------------:|--------------:|
| 0 | Off Drive | 202 | 330 | 532 |
| 1 | On Drive | 3 | 10 | 13 |
| 2 | Cut / Square Drive | 377 | 594 | 971 |
| 3 | Glance | 155 | 202 | 357 |
| 4 | Hook | 309 | 514 | 823 |
| 5 | Block | 84 | 163 | 247 |
| **Total** | | **1,130** | **1,813** | **2,943** |

---

# Front Foot Shots

The table below summarises the distribution of **front foot** batting shots by handedness and stroke type.

| Stroke ID | Stroke | Left-Handed | Right-Handed | Total Samples |
|-----------|--------|------------:|-------------:|--------------:|
| 0 | Off Drive | 380 | 755 | 1,135 |
| 1 | On Drive | 305 | 491 | 796 |
| 2 | Cut / Square Drive | 500 | 862 | 1,362 |
| 3 | Glance | 230 | 454 | 684 |
| 4 | Hook | 0 | 3 | 3 |
| 5 | Block | 398 | 893 | 1,291 |
| N/A | Not Specified | 0 | 2 | 2 |
| **Total** | | **1,813** | **3,460** | **5,273** |

---

# Dataset Summary

| Category | Samples |
|----------|---------:|
| Front Foot Shots | 5,273 |
| Back Foot Shots | 2,943 |
| **Total Dataset Size** | **8,182** |

## Competency Labels

The competency score assigned to each batting sample is grouped into four performance categories:

- **0–3:** Poor
- **4–6:** Average
- **7–8:** Good
- **9–10:** Excellent
