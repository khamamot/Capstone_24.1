### Research Question
Can objects in images be reliably determined using YOLO (You Only Look Once) methods?

### Data Source
https://www.kaggle.com/datasets/a7madmostafa/bdd100k-yolo

This dataset comes from the original Berkeley DeepDrive (BDD100K) dataset, converted into YOLO-compatible annotations. The images were captured for the purpose of training and testing artificial intelligence, so the images are all from ground level, in a variety of weather conditions including sunny, overcast and rainy, differing sunlight conditions including both daytime, nighttime, and dusk/dawn, and from a variety of locations including New York, San Francisco, Berkley, and the Bay Area.

After looking at a random sample of more then 100 of the images, they all appear to be captured from dash-cams mounted on cars. They constitute a wide range of times of day, weather conditions, lighting conditions, and traffic patterns. While the dataset contains a wide range of urban conditions, it fails to contain significant suburban and rural conditions that autonomous vehicles will eventually encounter.

### Metrics Used For Analyzing Results
The two metrics I used to analyze the results are mAP50 and mAP50-95. mAP50 stands for mean Average Precision with an Intersection of Union >= 0.50, basically was the object roughly found (the overlay of the predicted bounding box and the true bounding box are at least 50%.) mAP50-95 is similar, but more strict, evaluation the threshholds over multiple Intersections of Union between 0.50 and 0.95.

Expected ranges:
|          | Okay     | Good      | Excellent |
|----------|----------|-----------|-----------|
| mAP50    | ~0.5-0.6 | ~0.7-0.85 | ~0.85+    |
| mAP50-95 | ~0.3-0.5 | ~0.5-0.7  | ~0.7+     |

### Expected Results
I expect to be able to identify objects with at least mAP50s of 0.7 and mAP50-95 of 0.5

### Why Is This Question Important
This is important for use in autonomous vehicles being able to detect and identify nearby objects that may need to be avoided (such as other cars) or may hold important information (such as traffic lights). As autonomous vehicles become more prevalent, more accurate object identification methods will be more crucial.

### Results
After 100 epochs, YOLO reached the following results:
| Object Type   | Precision | Recall | mAP50 | mAP50-95 |
|---------------|-----------|--------|-------|----------|
| Person        | 0.726     | 0.452  | 0.547 | 0.262    |
| Car           | 0.769     | 0.693  | 0.758 | 0.467    |
| Traffic Light | 0.653     | 0.569  | 0.585 | 0.211    |
| Traffic Sign  | 0.714     | 0.533  | 0.606 | 0.310    |

Cars were the only objects that succeeded in being roughly detected and nothing was precicely detected.

### Summary
100 epochs were insufficient to train the YOLO model to reach the desired level of reliability, but seeing how the numbers were continuing to improve with each epoch, increasing the number of epochs may yeild the desired results.
