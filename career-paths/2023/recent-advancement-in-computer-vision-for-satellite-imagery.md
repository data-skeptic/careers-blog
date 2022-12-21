# Recent Advancement in Computer Vision for Satellite Imagery

Satellite images have found tremendous application in machine learning over the last couple of years. They possess an incredible amount of information about the earth's landscape and can be used to train computer vision models for a wide range of purposes such as predicting poverty levels in a region, estimating crop yield, retail forecasting, estimating the world crude oil inventory, and so on.

As expected, the research in this field is ever-growing. In this article, we will discuss some of the advancements in computer vision for satellite imagery that has happened in the last year. We’d begin by discussing a popular dataset used for machine learning research in remote sensing — the Sentinel-2 dataset.

## What is the Sentinel-2 Dataset?

The Sentinel-2 dataset is a set of high-resolution images gotten from the Sentinel-2 satellite of the [Copernicus program](https://www.copernicus.eu/en). The Sentinel satellites are twin satellites flying in the same orbit to the earth at 180 degrees phase. The satellites capture the state of the earth at 13 spectral bands with a revisit frequency of 5 days.

The dataset is typically used to study changes across the earth such as the changes in soil, vegetation, or water masses. The Sentinel-2 dataset can be downloaded [here](https://scihub.copernicus.eu/dhus/#/home) after creating an account.

Let’s now discuss how researchers use this dataset and more for machine learning purposes.

## 1. Detecting Landslide
    

Remote sensing has always found application in natural disaster applications. The [Landslide4sense](https://www.iarai.ac.at/landslide4sense/challenge/) is a challenge that promotes building machine learning models for detecting landslides using remote sensing images. Participants for the 2022 edition trained landslide-detecting models from the 14 bands of the [Sentinel-2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2), slope data from [ALOS PALSAR](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-radar-alos-palsar-radar-processing-system), and the digital elevation model from ALOS PALSAR.

The first-place team for the competition, the Kingdome team, developed a computer vision model with an F1 score of 74.54% on the test dataset. This is a massive improvement from the baseline approach results which had an F1-score of 59.92%. Their model underwent two data preprocessing techniques — the separated normalization technique to normalize the data and scale promotion for improving the resolution of the dataset from 128 by 1228 pixels to 512 by 512 pixels. The separated normalization technique involves using the respective mean and standard deviation of the training, testing, and validation set to normalize the training, testing, and validation data. Scale promotion on the other hand was used to counter the weak representation of small representation in the dataset. The model itself was an ensemble of Swin Transformer, EfficientNetV2, and SegFormer. 

The staggering improvement from this year's result further cements the massive potential satellite imagery wields. Early detection of landslides is critical in ameliorating their consequences which may include but are not limited to flooding, and earthquakes.

You can learn more about this research [here](https://arxiv.org/pdf/2209.02556.pdf).

## 2. Long Truck Traffic Detection
    

Satellite imagery can be used to detect traffic from commercial vehicles. In a [research](https://www.climatechange.ai/papers/icml2021/19) by Moritz Blattner, the Sentinel-2 dataset from 33 locations on Swiss freeway sections was used to build deep learning for detecting and predicting commercial vehicle traffic. Since commercial vehicles contribute about 7% to global CO2 emissions, estimating the count of commercial vehicles can help plan road maintenance, traffic congestion, and global warming policies. The result of the study can also be used to measure freight vehicle activities within a region.

A slightly tweaked Faster R-CNN model with RestNet50 was used to detect and count the commercial vehicles from the satellite imagery. After training, the model was able to identify commercial vehicles with a precision of 72%. Next, a gradient-boosted CatBoost model was used to estimate the hourly traffic rate of commercial vehicles at a given time.

In addition, the [Swiss automatic road traffic counts (SARTC)](https://www.astra.admin.ch/astra/en/home/documentation/data-and-information-products/traffic-data/data-and-publication/swiss-automatic-road-traffic-counts--sartc-.html) data was used as ground truth and for evaluating the model’s performance. This data collects the daily and weekly traffic volume of 330 traffic counting stations. The model was able to make predictions of traffic volumes for any freeway within 65% of the actual value.

The model however had a limitation. When there is more than 20% cloud in the satellite image or when the freeway section is longer than 1 kilometer, the model’s performance appreciably drops. It was however noted that the model performs best with less than 20% cloud in the satellite image and for freeway sections longer than 1 kilometer. 

You can learn more about the research [here](https://s3.us-east-1.amazonaws.com/climate-change-ai/papers/icml2021/19/paper.pdf).

## 3. Enabling the Combination of Two Satellite Images for Better Object Detection
    

Satellite imagery holds incredible information, but sadly, holds only when there is little or no cloud. Clouds can significantly mar the potential of satellite imagery. Since we cannot control the presence of clouds in a region, the onus is on us to provide a workaround despite the presence of clouds. Researchers have found that augmenting satellite imagery from different sources can increase the availability of cloud-free images. But since the sensors on satellites differ, images from different satellites may not be entirely compatible.

[This research](https://arxiv.org/abs/2210.07654) however explored the possibility of combining images from two major satellite imaging projects — Sentinel-2 and Landsat-8. The goal was to minimize both spatial and spectral differences from images on both satellites so that they can be combined for optimum performance. [Research](https://dl.acm.org/doi/10.1145/3390462) has shown that enhancing the resolution from low resolution to high-resolution improves the information the satellite imagery holds. This is a process called image super-resolution. The authors of this research used U-Net and Efficient Super Resolution Transformer (ESRT) to perform super-resolution and compared a baseline combined image with low-resolution. The U-Net model outperformed the other models with a Structural Similarity Index Measure (SSIM) of 91.14%. ESRT had an SSIM of 88.98% while the baseline model stood at 87.83%.

The result from this research is useful in various remote sensing applications such as crop health monitoring, forest supplies estimation, forest fire control, and so on. 

You can learn more about this research [here](https://arxiv.org/abs/2210.07654).

## 4. Automatically correcting road maps
    

Maintaining road networks on a satellite image is a pretty demanding task. In a developing country where there are no clear-cut roads or the road networks are ever-changing, it is even more difficult to keep up with the changes. This is why road maps from satellite imagery are incomplete or faulty. In [this research](https://arxiv.org/abs/2211.06544), the authors trained a machine learning model that could automatically fill up incomplete road networks in a map using image painting.

The dataset used was the [Massachusetts Road Geometry data](https://www.mass.gov/info-details/massgis-data-massachusetts-department-of-transportation-massdot-roads) which covers more than 2600 km of road networks in the region, including diverse rural, urban, and suburban areas. They trained this dataset on three models: the vanilla GLCIC (Globally and Locally Consistent Image Completion) as the baseline model, a GLCRC (Globally and Locally Consistent Road map Completion) model with a modified architecture, and a personalized GLCRC model.

The performance of the models was evaluated based on the correctness, completeness, and quality of straight roads, curvy roads, T-junctions, and an intersection. Their personalized GLCRC model had higher correctness, completeness, and quality for straight roads, T-junctions, and intersections. While for curvy roads, their model had a correctness of 0.754 while vanilla GLCIC and GLCRC had a correctness of 0.762 and 0.723 respectively. The entire result is shown in the table below.


| Road type     | Method                  | Correctness | Completeness | Quality |
|---------------|-------------------------|-------------|--------------|---------|
| Straight road | Vanilla GLCIC           | 0.787       | 0.786        | 0.649   |
|               | GLCRC                   | 0.750       | 0.806        | 0.635   |
|               | GLCRC + L (their model) | 0.894       | 0.898        | 0.811   |
| Curvy road    | Vanilla GLCIC           | 0.762       | 0.757        | 0.613   |
|               | GLCRC                   | 0.723       | 0.789        | 0.606   |
|               | GLCRC + L (their model) | 0.754       | 0.766        | 0.613   |
| T-junction    | Vanilla GLCIC           | 0.775       | 0.788        | 0.642   |
|               | GLCRC                   | 0.785       | 0.792        | 0.651   |
|               | GLCRC + L (their model) | 0.842       | 0.849        | 0.733   |
| Intersection  | Vanilla GLCIC           | 0.775       | 0.788        | 0.642   |
|               | GLCRC                   | 0.785       | 0.792        | 0.651   |
|               | GLCRC + L (their model) | 0.786       | 0.793        | 0.652   |
  

You can learn more about this research [here](https://arxiv.org/abs/2211.06544).

## 5. Predicting Air Quality
    

Unlike other environmental problems such as landslides, earthquakes, and flooding, air pollution is not visible to the eye. This makes measurement more difficult. Air quality monitoring stations measure air quality quite accurately. However, they require wide spaces and are not installed in developing areas. This calls for an automated way of measuring air quality irrespective of location or population density.

In [this research](https://arxiv.org/abs/2211.00780), the authors explored the possibility of predicting air quality using deep learning approaches. They used the Sentinel-2 dataset, Sentinel-5P dataset, and a tabular dataset containing altitude, population density, area type, and other geographical properties. After concatenating these data with a customized deep learning model (called AQNet), it outputs the estimated value of the nitrogen dioxide level, ozone level, and particulate matter 10 (PM10). The performance of their model is shown in the table below.

  

| Model              | Observation | Pre-training    | R2   | MAE  | MSE   |
|--------------------|-------------|-----------------|------|------|-------|
| Local              | 3000        | -               | 0.65 | 5.18 | 48.01 |
| Open steet map     | 3000        | -               | 0.34 | 7.22 | 88.29 |
| Satellite          | 3100        | BigEarth (LULC) | 0.57 | 5.50 | 58.47 |
| AQNet (No tabular) | 1300        | ImageNet        | 0.61 | 3.93 | 28.49 |
| AQNet              | 1300        | ImageNet        | 0.55 | 4.37 | 33.59 |
| AQNet-Single       | 1300        | ImageNet        | 0.66 | 3.72 | 25.28 |

You can learn more about the research [here](https://arxiv.org/pdf/2211.00780.pdf).

## Wrapping up

Satellite imagery has been seeing a number of unconventional applications of late. Of course, remote sensing images are still plagued with inherent issues such as getting covered by clouds, different light intensity, variance in shadow cast, etc. But despite these, the possibilities of remote sensing imagery when combined with machine learning techniques are far-reaching. 