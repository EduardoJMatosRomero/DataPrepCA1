# APS-Failure-at-Scania-Trucks

The datasets' positive class consists of component failures for a specific component of the APS system. The negative class consists of trucks with failures for components not related to the APS.

# Introduction

- The dataset consists of data collected from heavy Scania trucks in everyday usage. The system in focus is the Air Pressure system (APS) which generates pressurised air that are utilized in various functions in a truck, such as braking and gear changes. The datasets' positive class consists of component failures for a specific component of the APS system. The negative class consists of trucks with failures for components not related to the APS. The data consists of a subset of all available data, selected by experts.

- Challenge metric

Cost-metric of miss-classification:

Predicted class | True class | | pos | neg | pos | - | Cost_1 | neg | Cost_2 | - |

Cost_1 = 10 and cost_2 = 500

The total cost of a prediction model the sum of 'Cost_1' multiplied by the number of Instances with type 1 failure and 'Cost_2' with the number of instances with type 2 failure, resulting in a 'Total_cost'.

In this case Cost_1 refers to the cost that an unnessecary check needs to be done by an mechanic at an workshop, while Cost_2 refer to the cost of missing a faulty truck, which may cause a breakdown.

Total_cost = Cost_1No_Instances + Cost_2No_Instances.

## EDA

### NaN cleaning

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture1.JPG)

![image](https://github.com/EduardoJMatosRomero/DataPrepCA1/blob/main/Images/Capture2.JPG)

It is clear that NaN values appear in the dataset as 'na' and are of type 'object', and they are being replaced by np.NaN.





