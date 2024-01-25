# APS-Failure-at-Scania-Trucks

The datasets' positive class consists of component failures for a specific component of the APS system. The negative class consists of trucks with failures for components not related to the APS.

# Introduction

The dataset consists of data collected from heavy Scania trucks in everyday usage. The system in focus is the Air Pressure system (APS) which generates pressurised air that are utilized in various functions in a truck, such as braking and gear changes. The datasets' positive class consists of component failures for a specific component of the APS system. The negative class consists of trucks with failures for components not related to the APS. The data consists of a subset of all available data, selected by experts.

- Challenge metric

Cost-metric of miss-classification:

Predicted class | True class | | pos | neg | pos | - | Cost_1 | neg | Cost_2 | - |

Cost_1 = 10 and cost_2 = 500

The total cost of a prediction model the sum of 'Cost_1' multiplied by the number of Instances with type 1 failure and 'Cost_2' with the number of instances with type 2 failure, resulting in a 'Total_cost'.

In this case Cost_1 refers to the cost that an unnessecary check needs to be done by an mechanic at an workshop, while Cost_2 refer to the cost of missing a faulty truck, which may cause a breakdown.

Total_cost = Cost_1No_Instances + Cost_2No_Instances.

## EDA & Data Cleaning

Our dataset has 60000 entries, 59000 of them classified as True and 1000 classified as False class. 

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture3.JPG)

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture4.JPG)

### NaN cleaning

It is clear that NaN values appear in the dataset as 'na' and are of type 'object', and they are being replaced by np.NaN.

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture1.JPG)

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture2.JPG)

To ensure a clear database for our predictions, it has been decided to remove columns with more than 70% NaN values. This reduces the number of columns from 171 to 161.
 
![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture6.JPG)

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture5.JPG)

## Data Cleaning

The median was chosen to handle NaN values because it is more robust and not sensitive to outliers, making it suitable for skewed data.

It has been decided to use MinMaxScaler to normalise the data

### PCA

PCA is a technique that seeks the optimal number of features to achieve the best outcome from our algorithms. Having too many features may lead to poor algorithm performance.

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture7.JPG)

From our PCA analysis, we have determined that the optimal number of features is 80.

## Machine learning classification algorithms analysis.

### Classification algorithms - Random Forest

We have decided to use Random forest algorithms to classify our data.

The Random Forest algorithms have accurately predicted 98.31% of the data test set. It is worth noting that the algorithms have shown a tendency to mispredict false negatives rather than false positives, with 203 out of 12,000 values being incorrectly identified.¶
(12000 values=20% dataset=Test Data)

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture8.JPG)

The output shows the Random Forest (RF) model's performance in 10-fold cross-validation on training data. It achieved a high average accuracy of 98.3333% with very low variability (standard deviation of 0.000132), indicating consistent and reliable predictions across different subsets of the training data.

### Random forest classification Analysis.

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture9.JPG)

Performing machine learning and classification algorithms, we have developed an analysis that has enabled us to create a model with the ability to:

- Minimise the occurrence of missed maintenance of our lorries with specific APS system component failures by bringing them to the mechanic promptly and regularly.

- Identify that this happens in only 1.72% (where 12000=100% and 203=1.72%) of the occasions when we miss a faulty tuck.

