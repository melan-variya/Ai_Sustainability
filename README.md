# Land Use Classification - Delhi-NCR Airshed Analysis

## Project Overview

This project builds an automated pipeline to classify land use patterns in the Delhi-NCR region using satellite imagery and deep learning.

## Dataset

- Delhi-NCR region shapefile (EPSG:4326)
- Sentinel-2 RGB satellite images (128x128 pixels, 10m resolution)
- ESA WorldCover 2021 land cover raster
- Image filenames contain latitude and longitude coordinates

## Tasks

### Task 1: Spatial Gridding and Filtering

- Create 60km x 60km uniform grid over Delhi-NCR
- Filter satellite images that fall within region boundaries
- Visualize grid and region boundaries
- Output results: Grid plot and filtered image count

### Task 2: Label Construction

- Extract 128x128 land cover patches centered on each image
- Assign dominant land use class (mode) as label
- Map ESA class codes to categories (10=Tree cover, 50=Built-up, etc)
- Split data into 60% train, 40% test
- Visualize class distribution in both sets

### Task 3: Model Training and Evaluation

- Train a CNN model for land use classification
- 3 convolutional layers (16, 32, 64 filters)
- 2 fully connected layers (128 hidden, output classes)
- Evaluate using accuracy and F1-score
- Generate confusion matrix to analyze misclassifications

## Requirements

- Python 3.7+
- geopandas
- rasterio
- torch
- torchvision
- scikit-learn
- matplotlib
- seaborn
- pandas
- numpy

## Installation

```
pip install geopandas rasterio torch torchvision scikit-learn matplotlib seaborn pandas numpy
```

## Usage

Update file paths in code to point to your local data:

- delhi_ncr_region.geojson
- images_folder/rgb/ (containing PNG images)
- worldcover_bbox_delhi_ncr_2021.tif (land cover raster)

Run notebook: Open Ai_Sustainability.ipynb in Jupyter/VS Code and execute cells

## Output

- Grid visualization (60km cells overlayed on region)
- Class distribution plots (train and test sets)
- Model training loss per epoch
- Test accuracy and F1-score
- Classification report (precision, recall, F1 per class)
- Confusion matrix heatmap

## Results

Model is trained for 5 epochs with Adam optimizer (lr=0.001) with accuracy of around 85%.
Trained model is saved and can be reused on subsequent runs.
Evaluation metrics show model performance on test set.

## Notes

- All coordinates use UTM zone 44 (EPSG:32644) for spatial operations
- Land cover mode is computed from 128x128 patches extracted from raster
- CNN uses MaxPooling to progressively reduce spatial dimensions
- Training uses CrossEntropyLoss with balanced class handling


Note: Used AI for research purpose only