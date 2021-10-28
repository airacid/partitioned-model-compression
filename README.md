#  Partition of YOLOv3_TensorFlow
## Modification

Implementation on initial version of partitioning neural network, feature map compression.
This is modification of repo: [YOLOv3_tensorflow](https://github.com/wizyoung/YOLOv3_TensorFlow).
-------


## Idea of Network Partitioning
![image](https://user-images.githubusercontent.com/38776966/139167357-e3691393-f385-4500-a6d3-121763a046f7.png)

- Partitioning of an AI model
   - Divide a neural network 
   - Save partial networks to separate models
   - Deliver intermediate data between them 
- Pros and cons of AI model partitioning
  - Pros: Small device computing resources comparing to the original model
  - Cons: One additional transmission of intermediate data
- Consideration on the Intermediate Data
  - Intermediate data size depends on the layer where division occurs
  - If that layer has many neurons, intermediate data size will increase
- Intermediate Data Compression Method 
  - To reduce the effect of intermediate data transmission


## Process of Feature Map Compression & Decompression
![image](https://user-images.githubusercontent.com/38776966/139167379-4963cf4f-6193-43ba-a58f-94c9935e7829.png)

- Sender: Sparsification – Quantization - Entropy Coding 
- Receiver: Decoding and dequantization

## Results

|                       |     Original result    |     w/o quantization    |     Final compression result    |
|-----------------------|:----------------------:|:-----------------------:|:-------------------------------:|
|     Feature   size    |        4,377   KB      |        2,799   KB       |              598 KB             |
|     Data   type       |        float   32      |        float   32       |              uint 8             |
|     map   on COCO     |           0.66         |             -           |               0.58              |

## Credits:

I refer to many fantastic repos during the implementation:

https://github.com/wizyoung/YOLOv3_TensorFlow

https://github.com/YunYang1994/tensorflow-yolov3

https://github.com/qqwweee/keras-yolo3

https://github.com/eriklindernoren/PyTorch-YOLOv3

https://github.com/pjreddie/darknet





 
