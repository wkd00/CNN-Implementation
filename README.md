# CNN Implementation

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
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d (Conv2D)             (None, 222, 222, 32)      896       
                                                                 
 max_pooling2d (MaxPooling2  (None, 111, 111, 32)      0         
 D)                                                              
                                                                 
 batch_normalization (Batch  (None, 111, 111, 32)      128       
 Normalization)                                                  
                                                                 
 conv2d_1 (Conv2D)           (None, 109, 109, 64)      18496     
                                                                 
 max_pooling2d_1 (MaxPoolin  (None, 54, 54, 64)        0         
 g2D)                                                            
                                                                 
 batch_normalization_1 (Bat  (None, 54, 54, 64)        256       
 chNormalization)                                                
                                                                 
 conv2d_2 (Conv2D)           (None, 52, 52, 128)       73856     
                                                                 
 max_pooling2d_2 (MaxPoolin  (None, 26, 26, 128)       0         
 g2D)                                                            
                                                                 
...
Total params: 11178945 (42.64 MB)
Trainable params: 11178113 (42.64 MB)
Non-trainable params: 832 (3.25 KB)
_________________________________________________________________



## 3. Tenary Model 

### Attempt 1. 
- No data augmentation
- Train accuracy: 0.9836
- Validation accuracy: 0.6800
  
Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d (Conv2D)             (None, 222, 222, 64)      1792      
                                                                 
 max_pooling2d (MaxPooling2  (None, 111, 111, 64)      0         
 D)                                                              
                                                                 
 conv2d_1 (Conv2D)           (None, 109, 109, 128)     73856     
                                                                 
 max_pooling2d_1 (MaxPoolin  (None, 54, 54, 128)       0         
 g2D)                                                            
                                                                 
 conv2d_2 (Conv2D)           (None, 52, 52, 256)       295168    
                                                                 
 max_pooling2d_2 (MaxPoolin  (None, 26, 26, 256)       0         
 g2D)                                                            
                                                                 
 flatten (Flatten)           (None, 173056)            0         
                                                                 
 dense (Dense)               (None, 256)               44302592  
                                                                 
 dropout (Dropout)           (None, 256)               0         
                                                                 
...
Total params: 44715210 (170.57 MB)
Trainable params: 44715210 (170.57 MB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________


### Attempt 2.
- No data augmentation
- Train accuracy: 0.9645
- validation accuracy: 0.6800

Model: "sequential_12"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d_45 (Conv2D)          (None, 222, 222, 32)      896       
                                                                 
 max_pooling2d_45 (MaxPooli  (None, 111, 111, 32)      0         
 ng2D)                                                           
                                                                 
 conv2d_46 (Conv2D)          (None, 109, 109, 64)      18496     
                                                                 
 max_pooling2d_46 (MaxPooli  (None, 54, 54, 64)        0         
 ng2D)                                                           
                                                                 
 conv2d_47 (Conv2D)          (None, 52, 52, 128)       73856     
                                                                 
 max_pooling2d_47 (MaxPooli  (None, 26, 26, 128)       0         
 ng2D)                                                           
                                                                 
 conv2d_48 (Conv2D)          (None, 24, 24, 256)       295168    
                                                                 
 max_pooling2d_48 (MaxPooli  (None, 12, 12, 256)       0         
 ng2D)                                                           
                                                                 
 flatten_12 (Flatten)        (None, 36864)             0         
...
Total params: 9869418 (37.65 MB)
Trainable params: 9869418 (37.65 MB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________

### Attempt 3. 
- No data augmentation
- Train accuracy: 0.8853
- Validation accuracy: 0.5700

Model: "sequential_3"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 vgg16 (Functional)          (None, 7, 7, 512)         14714688  
                                                                 
 flatten_3 (Flatten)         (None, 25088)             0         
                                                                 
 dense_12 (Dense)            (None, 256)               6422784   
                                                                 
 dropout_9 (Dropout)         (None, 256)               0         
                                                                 
 dense_13 (Dense)            (None, 10)                2570      
                                                                 
=================================================================
Total params: 21140042 (80.64 MB)
Trainable params: 21140042 (80.64 MB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________

### Attempt 4. 
- Image size: 224 * 224 * 3 -> 64 * 64 * 3
- Data Augmentation on Training dataset:
    rotation_range=10,
    width_shift_range=0.05,
    height_shift_range=0.05,
    zoom_range=0.05,
    horizontal_flip=True,
    fill_mode='nearest'
- Train accuracy: 0.8703
- Validation accuracy: 0.7800

Model: "sequential_12"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d_30 (Conv2D)          (None, 62, 62, 64)        1792      
                                                                 
 conv2d_31 (Conv2D)          (None, 60, 60, 128)       73856     
                                                                 
 max_pooling2d_30 (MaxPooli  (None, 30, 30, 128)       0         
 ng2D)                                                           
                                                                 
 conv2d_32 (Conv2D)          (None, 28, 28, 256)       295168    
                                                                 
 max_pooling2d_31 (MaxPooli  (None, 14, 14, 256)       0         
 ng2D)                                                           
                                                                 
 flatten_12 (Flatten)        (None, 50176)             0         
                                                                 
 dense_45 (Dense)            (None, 128)               6422656   
                                                                 
 dense_46 (Dense)            (None, 64)                8256      
                                                                 
 dense_47 (Dense)            (None, 32)                2080      
                                                                 
 dense_48 (Dense)            (None, 10)                330       
...
Total params: 6804138 (25.96 MB)
Trainable params: 6804138 (25.96 MB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________

### Attempt 5. 
- Image size: 36 * 36 * 3
- No data augmentation
- Train accuracy: 0.8792 
- Validation accuracy: 0.8100 (Highest!)

Model: "sequential_7"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d_22 (Conv2D)          (None, 36, 36, 32)        896       
                                                                 
 batch_normalization_22 (Ba  (None, 36, 36, 32)        128       
 tchNormalization)                                               
                                                                 
 re_lu_22 (ReLU)             (None, 36, 36, 32)        0         
                                                                 
 max_pooling2d_13 (MaxPooli  (None, 18, 18, 32)        0         
 ng2D)                                                           
                                                                 
 conv2d_23 (Conv2D)          (None, 18, 18, 64)        18496     
                                                                 
 batch_normalization_23 (Ba  (None, 18, 18, 64)        256       
 tchNormalization)                                               
                                                                 
 re_lu_23 (ReLU)             (None, 18, 18, 64)        0         
                                                                 
 max_pooling2d_14 (MaxPooli  (None, 9, 9, 64)          0         
 ng2D)                                                           
                                                                 
 conv2d_24 (Conv2D)          (None, 9, 9, 128)         73856     
...
Total params: 652874 (2.49 MB)
Trainable params: 652426 (2.49 MB)
Non-trainable params: 448 (1.75 KB)
_________________________________________________________________ 

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
