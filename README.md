# CNN Implementation

## 0. Introduction 
- A project conducted in a Deep Learning course within the Department of Applied Statistics.

## 1. Dataset
- 100 Sports Image Classification (https://www.kaggle.com/datasets/gpiosenka/sports-classification)
- Used only 10 sports(fencing, golf, hockey, rugby, ski-jumping, swimming, table tennis, tennis, volleyball, weightlifting)
- Image size: 224 * 224 * 3


## 2. Binary Model
- Before building a model to classify 10 sports, started with a model to classify 2 sports(hockey, tennis) for experimental purposes.
- No data augmentation
- Train accuracy: 0.9571
- Validation Accuracy: 1


Model: "sequential"


| Layer (Type)                 | Output Shape         | Param #    |
|------------------------------|----------------------|------------|
| `conv2d (Conv2D)`            | (None, 222, 222, 32) | 896        |
| `max_pooling2d (MaxPooling2D)` | (None, 111, 111, 32) | 0          |
| `batch_normalization (BatchNormalization)` | (None, 111, 111, 32) | 128        |
| `conv2d_1 (Conv2D)`          | (None, 109, 109, 64) | 18496      |
| `max_pooling2d_1 (MaxPooling2D)` | (None, 54, 54, 64)   | 0          |
| `batch_normalization_1 (BatchNormalization)` | (None, 54, 54, 64)   | 256        |
| `conv2d_2 (Conv2D)`          | (None, 52, 52, 128)  | 73856      |
| `max_pooling2d_2 (MaxPooling2D)` | (None, 26, 26, 128)  | 0          |
| `batch_normalization_2 (BatchNormalization)` | (None, 26, 26, 128)  | 512        |
| `flatten (Flatten)`          | (None, 86528)        | 0          |
| `dense (Dense)`              | (None, 128)          | 11075712   |
| `dropout (Dropout)`          | (None, 128)          | 0          |
| `batch_normalization_3 (BatchNormalization)` | (None, 128)          | 512        |
| `dense_1 (Dense)`            | (None, 64)           | 8256       |
| `dropout_1 (Dropout)`        | (None, 64)           | 0          |
| `batch_normalization_4 (BatchNormalization)` | (None, 64)           | 256        |
| `dense_2 (Dense)`            | (None, 1)            | 65         |
| **Total params** |                      | 11178945   |
| **Trainable params** |                      | 11178113   |
| **Non-trainable params** |                      | 832        |


## 3. Tenary Model 

### Attempt 1. 
- No data augmentation
- Train accuracy: 0.9836
- Validation accuracy: 0.6800
  
Model: "sequential"

| Layer (Type)                 | Output Shape         | Param #    |
|------------------------------|----------------------|------------|
| `conv2d (Conv2D)`            | (None, 222, 222, 64) | 1792       |
| `max_pooling2d (MaxPooling2D)` | (None, 111, 111, 64) | 0          |
| `conv2d_1 (Conv2D)`          | (None, 109, 109, 128)| 73856      |
| `max_pooling2d_1 (MaxPooling2D)` | (None, 54, 54, 128)  | 0          |
| `conv2d_2 (Conv2D)`          | (None, 52, 52, 256)  | 295168     |
| `max_pooling2d_2 (MaxPooling2D)` | (None, 26, 26, 256)  | 0          |
| `flatten (Flatten)`          | (None, 173056)       | 0          |
| `dense (Dense)`              | (None, 256)          | 44302592   |
| `dropout (Dropout)`          | (None, 256)          | 0          |
| `dense_1 (Dense)`            | (None, 128)          | 32896      |
| `dropout_1 (Dropout)`        | (None, 128)          | 0          |
| `dense_2 (Dense)`            | (None, 64)           | 8256       |
| `dropout_2 (Dropout)`        | (None, 64)           | 0          |
| `dense_3 (Dense)`            | (None, 10)           | 650        |
| **Total params** |                      | 44715210   |
| **Trainable params** |                      | 44715210   |
| **Non-trainable params** |                      | 0          |


### Attempt 2.
- No data augmentation
- Train accuracy: 0.9645
- validation accuracy: 0.6800

Model: "sequential_12"

| Layer (Type)                 | Output Shape         | Param #    |
|------------------------------|----------------------|------------|
| `conv2d_45 (Conv2D)`         | (None, 222, 222, 32) | 896        |
| `max_pooling2d_45 (MaxPooling2D)` | (None, 111, 111, 32) | 0          |
| `conv2d_46 (Conv2D)`         | (None, 109, 109, 64) | 18496      |
| `max_pooling2d_46 (MaxPooling2D)` | (None, 54, 54, 64)   | 0          |
| `conv2d_47 (Conv2D)`         | (None, 52, 52, 128)  | 73856      |
| `max_pooling2d_47 (MaxPooling2D)` | (None, 26, 26, 128)  | 0          |
| `conv2d_48 (Conv2D)`         | (None, 24, 24, 256)  | 295168     |
| `max_pooling2d_48 (MaxPooling2D)` | (None, 12, 12, 256)  | 0          |
| `flatten_12 (Flatten)`       | (None, 36864)        | 0          |
| `dense_58 (Dense)`           | (None, 256)          | 9437440    |
| `dropout_46 (Dropout)`       | (None, 256)          | 0          |
| `dense_59 (Dense)`           | (None, 128)          | 32896      |
| `dropout_47 (Dropout)`       | (None, 128)          | 0          |
| `dense_60 (Dense)`           | (None, 64)           | 8256       |
| `dropout_48 (Dropout)`       | (None, 64)           | 0          |
| `dense_61 (Dense)`           | (None, 32)           | 2080       |
| `dropout_49 (Dropout)`       | (None, 32)           | 0          |
| `dense_62 (Dense)`           | (None, 10)           | 330        |
| **Total params** |                      | 9869418    |
| **Trainable params** |                      | 9869418    |
| **Non-trainable params** |                      | 0          |


### Attempt 3. 
- No data augmentation
- Train accuracy: 0.8853
- Validation accuracy: 0.5700

Model: "sequential_3"

| Layer (Type)                 | Output Shape         | Param #    |
|------------------------------|----------------------|------------|
| `vgg16 (Functional)`         | (None, 7, 7, 512)    | 14714688   |
| `flatten_3 (Flatten)`        | (None, 25088)        | 0          |
| `dense_12 (Dense)`           | (None, 256)          | 6422784    |
| `dropout_9 (Dropout)`        | (None, 256)          | 0          |
| `dense_13 (Dense)`           | (None, 10)           | 2570       |
| **Total params** |                      | 21140042   |
| **Trainable params** |                      | 21140042   |
| **Non-trainable params** |                      | 0          |

### Attempt 4. 
- Image size: 224 * 224 * 3 -> 64 * 64 * 3
- Data Augmentation on Training dataset:
  - rotation_range=10
  - width_shift_range=0.05
  - height_shift_range=0.05
  - zoom_range=0.05
  - horizontal_flip=True
  - fill_mode='nearest'
- Train accuracy: 0.8703
- Validation accuracy: 0.7800

Model: "sequential_12"

| Layer (Type)                 | Output Shape         | Param #   |
|------------------------------|----------------------|-----------|
| `conv2d_30 (Conv2D)`         | (None, 62, 62, 64)   | 1792      |
| `conv2d_31 (Conv2D)`         | (None, 60, 60, 128)  | 73856     |
| `max_pooling2d_30 (MaxPooling2D)` | (None, 30, 30, 128)  | 0         |
| `conv2d_32 (Conv2D)`         | (None, 28, 28, 256)  | 295168    |
| `max_pooling2d_31 (MaxPooling2D)` | (None, 14, 14, 256)  | 0         |
| `flatten_12 (Flatten)`       | (None, 50176)        | 0         |
| `dense_45 (Dense)`           | (None, 128)          | 6422656   |
| `dense_46 (Dense)`           | (None, 64)           | 8256      |
| `dense_47 (Dense)`           | (None, 32)           | 2080      |
| `dense_48 (Dense)`           | (None, 10)           | 330       |
| **Total params** |                      | 6804138   |
| **Trainable params** |                      | 6804138   |
| **Non-trainable params** |                      | 0         |


### Attempt 5. 
- Image size: 36 * 36 * 3
- No data augmentation
- Train accuracy: 0.8792 
- Validation accuracy: 0.8100 (Highest!)

Model: "sequential_7"

| Layer (Type)                 | Output Shape         | Param #   |
|------------------------------|----------------------|-----------|
| `conv2d_22 (Conv2D)`         | (None, 36, 36, 32)   | 896       |
| `batch_normalization_22 (BatchNormalization)` | (None, 36, 36, 32)   | 128       |
| `re_lu_22 (ReLU)`            | (None, 36, 36, 32)   | 0         |
| `max_pooling2d_13 (MaxPooling2D)` | (None, 18, 18, 32)   | 0         |
| `conv2d_23 (Conv2D)`         | (None, 18, 18, 64)   | 18496     |
| `batch_normalization_23 (BatchNormalization)` | (None, 18, 18, 64)   | 256       |
| `re_lu_23 (ReLU)`            | (None, 18, 18, 64)   | 0         |
| `max_pooling2d_14 (MaxPooling2D)` | (None, 9, 9, 64)     | 0         |
| `conv2d_24 (Conv2D)`         | (None, 9, 9, 128)    | 73856     |
| `batch_normalization_24 (BatchNormalization)` | (None, 9, 9, 128)    | 512       |
| `re_lu_24 (ReLU)`            | (None, 9, 9, 128)    | 0         |
| `max_pooling2d_15 (MaxPooling2D)` | (None, 4, 4, 128)    | 0         |
| `flatten_7 (Flatten)`        | (None, 2048)         | 0         |
| `dense_24 (Dense)`           | (None, 256)          | 524544    |
| `dropout_17 (Dropout)`       | (None, 256)          | 0         |
| `dense_25 (Dense)`           | (None, 128)          | 32896     |
| `dropout_18 (Dropout)`       | (None, 128)          | 0         |
| `dense_26 (Dense)`           | (None, 10)           | 1290      |
| **Total params** |                      | 652874    |
| **Trainable params** |                      | 652426    |
| **Non-trainable params** |                      | 448       |

## 4. Testing on the best model(Attempt 5)
- Used self-taken photos for the test dataset.
- True: tennis -> Predicted: tennis
- True: golf -> Predicted: fencing (Incorrect)
- True: ski jumping -> Predicted: ski jumping
- True: tennis -> Predicted: table tennis (Incorrect)

## 5. Conclusion 
- Reducing the image size was more effective for performance than rapidly decreasing dimensions by using larger filter sizes in convolutional and pooling layers.
- Increasing the number of filters progressively also yielded better performance.
- Doesn't work well on self-taken photos
