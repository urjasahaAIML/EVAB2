
# S4-Assignment-Solution 

This is a MNIST (28X28X1 image) digit recognition network with:
- 99.4% validation accuracy
- 14.7k Parameters
- 2 MaxPooling,
- 3x3 Convolutions,
- Receptive Field calculation,
- Log_SoftMax,
- Variable Learning Rate,
- Batch Normalization,
- DropOut in training
- Less than 20 Epochs
- No fully connected layer
- GAP


## Details of the Model

- Started with 10 channels and max channels reached is 30 (parameter restriction)
- Padding in initial blocks
- Batch Normalization in every layer to capture non-dominant features
- 10% Dropout
- Reduce learning rate after 10 epochs to reduce oscillation of weights
