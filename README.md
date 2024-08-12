# OS_CMR-SS-SAX-NN-HEALTHY-VS-ICMP

Using Deep Learning to discriminate between healthy and ischemic cardiomyopathy (ICMP) cases from Oxygenation-sensitive cardiac magnetic resonance imaging (OS-CMR). 

## Dataset
- Dataset compiled by expert clinicians at the Royal Victoria Hospital of the McGill University Health Centre.
- 120 cases (50/50% class split).
- Each case has a single slice (SS) short-axis view (SAX) sequence of images.
- Each sequence has 20 images.
- Each image has a corresponding mask of the left ventricle (LV).
- Initial images were 256x256 pixels.

## Pre-processing
- From initial images, LV square area was extracted using mask min and max coordinate values.
- Resulting sequences were padded and stacked into a numpy array (20, 60, 60).
- Sequences were saved into the following dataset:

```
DL_CMR_NP/
        Healthy/
                1.npy
                2.npy
                ...
        ICMP/
                1.npy
                2.npy
                ...
```

## Neural Network
- Tenserflow 2.15.0

### Input Dataset
- Training/validation/testing split was 60/20/20%
- Training data augmented with left-right and up-down flips.
- Normalized with division by 255.

### Architecture
- NN had 3D Convolution and Pooling layers, see .ipynb file for details.
