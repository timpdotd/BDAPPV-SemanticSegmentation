# Semantic Segmentation of Solar Panels from Google Earth Imagery Using U-Net

## Description

The image segmentation task as the objective to identify the objective in a generic photo. This could be a multi-class or binary image segmentation: the first need to identify all the objectives in a photo, for example, the cat, the human, the table and so on; the second one need only to identify the object and what is not the object, for example the cat and the other things are "not the cat".

In this notebook we will explore the image segmentation on photovoltaic panels in multi spectral satellitar images. We will use a UNET model for the task (see later on) and compare the results to identify the best outcomes and the difference between the prediction and the truth label.

## About the dataset



### bdappv/ Root data folder
- google/ign:  One folder for each campaign
  - img/: Folder containing all the images presented to the users. This folder contains 28807 images for Google and 17325 images for IGN.
  - mask/: Folder containing all segmentations masks generated from the polygon annotations of the users. This folder contains 13303 masks for Google and 7686 masks for IGN.
- metadata.csv The .csv  file with the installations' metadata.

### data/ Root data folder

- raw/ Folder containing the raw crowdsourcing data and raw metadata;
  - input-google.json: .json input data data containing all information on images and raw annotators’ contributions for both phases (clicks and polygons) during the first annotation campaign;
  - input-ign.json: .json input data containing all information on images and raw annotators’ contributions for both phases (clicks and polygons) during the second annotation campaign;
  - raw-metadata.json: .json output containing the PV systems’ metadata extracted from the BDPV database before filtering. It can be used to replicate the association between the installations and the segmentation masks, as done in the notebook metadata.
- replication/ Folder containing the compiled data used to generate the segmentation masks;
  - campaign-google/campaign-ign: One folder for each campaign
    - click-analysis.json: .json output on the click analysis, compiling raw input into a few best-guess locations for the PV arrays. This dataset enables the replication of our annotations,
    - polygon-analysis.json: .json output of polygon analysis, compiling raw input into a best-guess polygon for the PV arrays.
- validation/ Folder containing the compiled data used for technical validation.
  - campaign-google/campaign-ign: One folder for each campaign
    - click-analysis-thres=1.0.json: .json output of the click analysis with a lowered threshold to analyze the effect of the threshold on image classification, as done in the notebook annotation;
    - polygon-analysis-thres=1.0.json: .json output of polygon analysis, with a lowered threshold to analyze the effect of the threshold on polygon annotation, as done in the notebook annotations.
  - metadata.csv: the .csv file of filtered installations' metadata.

## Summary

Photovoltaic (PV) energy generation plays a crucial role in the energy transition. Small-scale, residential PV installations are deployed at an unprecedented pace, and their safe integration into the grid necessitates up-to-date, high-quality information. Overhead imagery is increasingly used to improve the knowledge of residential PV installations with machine learning models capable of automatically mapping these installations. However, these models cannot be reliably transferred from one region or imagery source to another without incurring a decrease in accuracy. To address this issue, known as distribution shift, and foster the development of PV array mapping pipelines, we propose a dataset containing aerial images, segmentation masks, and installation metadata. We provide installation metadata for more than 28000 installations. We provide ground truth segmentation masks for 13000 installations, including 7000 with annotations for two different image providers. Finally, we provide installation metadata that matches the annotation for more than 8000 installations. Dataset applications include end-to-end PV registry construction, robust PV installations mapping, and analysis of crowdsourced datasets.

This dataset contains the complete records associated with the article "A crowdsourced dataset of aerial images of solar panels, their segmentation masks, and characteristics", published in Scientific data. The article is accessible here : https://www.nature.com/articles/s41597-023-01951-4

These complete records consist of:

1. The complete training dataset containing RGB overhead imagery, segmentation masks and metadata of PV installations (folder bdappv),
2. The raw crowdsourcing data, and the postprocessed data for replication and validation (folder data).
---
The description above is copied from the official page of the dataset.

The dataset can be found here: https://zenodo.org/records/7358126

The paper can be found here: https://www.nature.com/articles/s41597-023-01951-4

## You can find the original notebook here
Github repository: https://github.com/timpdotd/BDAPPV-SemanticSegmentation

Colab notebook: https://colab.research.google.com/drive/1BLcVOCoMeSydPXSgYOecfkTJ6dOLP5H0?usp=sharing
