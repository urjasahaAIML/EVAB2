
# S4-Assignment-Solution 

This is a MNIST (28X28X1 image) digit recognition network with:
- 99.4% validation accuracy
- 14.7k Parameters



## Highlights of the Model

- Started with 10 channels and max channels reached is 30 (parameter restriction)
- Padding in initial blocks
- Batch Normalization in every layer to capture non-dominant features
- 10% Dropout
- Reduce learning rate after 10 epochs to reduce oscillation of weights
- Please follw the .pybb notebook (https://github.com/tapasML/EVAB2/blob/main/S4/Assignment_Session_4_Arch.ipynb)  for details of code 


## Define the Network

Since parameters size is retricted, we can not suddenly expand and reduce channels in a layer, as it hurts learning weights. Instead start small (10 channels) and increase uniformly in baby steps.

Using padding in first two blocks, to preserve every pixel of information we got.

Block #1:

[Conv-> ReLU-> BatchNorm] -> [Conv-> ReLU-> BatchNorm] -> MaxPool -> Dropout

Block #2:

[Conv-> ReLU-> BatchNorm] -> [Conv-> ReLU-> BatchNorm] -> MaxPool -> Dropout

Block #3:

[Conv-> GAP]

Block #4:

[Flatten -> Log_SoftMax]

## Data dimension through the Network


        self.conv1 = nn.Conv2d(1,  10, 3, padding=1) #input:28X28X1, out:28X28X10,  kernel:3X3, RF: 3.<b>
        self.conv2 = nn.Conv2d(10, 10, 3, padding=1) #input:28X28X10, out:28X28X10, kernel:3X3, RF: 5.
        self.pool1 = nn.MaxPool2d(2, 2)              #input:28X28X10, out:14X14X10, kernel:2X2, RF: 10
        self.conv3 = nn.Conv2d(10, 20, 3, padding=1) #input:14X14X10, out:14X14X20, kernel:3X3, RF: 12.
        self.conv4 = nn.Conv2d(20, 20, 3, padding=1) #input:14X14X20, out:14X14X20, kernel:3X3, RF: 14.
        self.pool2 = nn.MaxPool2d(2, 2)              #input:14X14X20, out:7X7X20,   kernel:2X2, RF: 28
        self.conv5 = nn.Conv2d(20, 30, 3, padding=0) #input:7X7X20, out:5X5X30,     kernel:3X3, RF: 30.
        self.conv6 = nn.Conv2d(30, 10, 3)            #input:5X5X30, out:3X3X10,     kernel:3X3, RF: 32.        
        self.avg_pool = nn.AvgPool2d(kernel_size=3, stride=3)#input:3X3X10, out:1X1X10, kernel:3X3



'''

